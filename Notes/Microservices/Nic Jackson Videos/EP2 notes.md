## EP 2

[[Microservices by Nic Jackson]]

Move handlers into their own package.

Http handler is an interface with a single method on it, serveHTTP(). So to create a handler, create a struct that implements the interface. This means that this code that uses http.Handlefunc...
`
http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request){
		log.Println("Hello World")
		d, err := ioutil.Readall(r.Body)
		if err != nil {
			http.Error(w, "Ooops", http.StatusBadRequest)
			return
		}
		fmt.Fprintf(w, "Hello %s", d)
})
`


is the same as this code that satisfies the handler interface

`
type Hello struct {}

func (h *Hello) ServeHTTP(w http.ResponseWritter, r *http.Request){
	log.Println("Hello World")
	d, err := ioutil.Readall(r.Body)
	if err != nil {
		http.Error(w, "Ooops", http.StatusBadRequest)
		return
	}
	
	fmt.Fprintf(w, "Hello %s", d)
}
`

Dependency injection.

`
type Hello struct {
	l *log.Logger
}

func NewHello(l *log.Logger) *Hello {
	return &Hello{l}
}

func (h *Hello) ServeHTTP(w http.ResponseWritter, r *http.Request){
	h.l.Println("Hello World")
	d, err := ioutil.Readall(r.Body)
	if err != nil {
		http.Error(w, "Ooops", http.StatusBadRequest)
		return
	}
	
	fmt.Fprintf(w, "Hello %s", d)
}

`

In a test, can replace l with something else. When getting into connecting to database, need to use dependency injection so can write good unit tests.

`
func main(){
	// create a logger
	l := log.New(os.Stdout, "product-api", log.LstdFlags)
	// inject the logger into the handler
	hh := handlers.NewHello()
	// register the handler with the server
	sm := http.NewServeMux()
	sm.Handle("/", hh)
	http.ListenAndServe(":9090", sm)
}
`

In a service, server parameters should be tuned.
When a connection is made to your server, it's not free, it costs time. If you have a lot of requests from a single client you can keep that connection open. This is useful for when you have lots of microservices connecting to each other. TLS is a little more expensive to establish a connection than TCP.  When running service to service, have a higher idle time to keep connections alive.

`
l := log.New(os.Stdout, "product-api", log.LstdFlags)
hh := handlers.NewHello()
sm := http.NewServeMux()
sm.Handle("/", hh)

s := &http.Server{
	Addr: ":9090",
	Handler: sm,
	IdleTimeout: 120*time.Second,
	ReadTimeout: 1*time.Second,
	WriteTimeout: 1*time*Second,
}

s.ListenAndServe()
`

Graceful shutdown is really important. If there's a large upload or a database transaction, if not done gracefully then the risk is that a client is disconnected and they are not allowed to finish what they are doing. 
`
tc, _ := context.WithTimeout(context.Background(), 30*time.Second)
s.Shutdown(tc)
`
Tells the server to stop accepting new requests. Waits until the requests currently being handled by the server have completed.
Shutdown takes a context, in the example above, 30 seconds are given to allow requests to be processed, if processing is not complete within 30 seconds, forcefully close it. 

`s.ListenAndServe()` will block unless its wrapped in a goroutine, `go func()`
A goroutine is a lightweight thread managed by the Go runtime.
Goroutines run in the same address space, so access to shared memory must by synchronized.

`
// Listen and serve is in a Goroutine so it does not block.
go func(){
	err := s.ListenAndServe()
	if err != nil {
		l.fatal(err)
	}
}()

// create a channel
signChan := make(chan os.Signal)

// When a kill or an interupt is received, broadcast it to the channel.
signal.Notify(sigChan, os.Interupt)
signal.Notify(signChan, os.Kill)

// The next line blocks until a message is available to be consumed.
sig := <-sigChan
l.Println("Received terminate, graceful shutdown", sig)

tc, _ := context.WithTimeout(context.Background(), 30*time.Second)
s.Shutdown(tc)
`

