## EP 1
Looks like his setup is not too different to my own. I like how he uses VSCode liveshare.

`fmt.Fprintf()` can be used to print directly to a http.ResponseWriter.

When handling errors in API handlers, if `w` is a `http.ResponseWriter` 

instead of 
`
if err != nil {
	 w.WriteHeader(http.StatusBadRequest)
	 w.Write([]byte("Ooops"))
	 return
}
`

There's a convenience method in the http package called Error. The same code would be

`
if err != nil {
	http.Error(w, "Ooops", http.StatusBadRequest)
	return
}
`

