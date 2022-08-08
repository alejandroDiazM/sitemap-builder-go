# SITEMAP BUILDER

This program written in Go takes a website and builds a map of all the links and URLs you can go from the root page. You can set a limit for how deep the map needs to go, and it will output as many urls as there are within that max depth. For example, if we set the maximun depth to 3, only pages that we can reach within 3 steps will be included in the resulting XML.

This program makes use of another of my projects based on Jon Calhoun's Gophercises, so I recommend giving it a look at https://github.com/alejandrodaxians/html_link_parser.

<br>

## Usage:

To use the program, we need to set the environment first. For starters, we need to allow our main to reach the link module. To do that, run:

```
go mod init link
```

Perfect, now the internal dependencies work correctly. But our program makes use of the HTML package, which is not native to Golang. Therefor, we shall run the following command to install it:

```
go get -u golang.org/x/net/html
```
<br>

## Running:

Done! Now the program can run smoothly. Note that it works with XML, so if you run it with the command 

```
go run main/main.go
```
you'll get an output on XML format, but if you run something like:

```
go run main/main.go > map.xml
```
the output will go directly to a file called map.cml, on the project directory, which I find far more useful.

<br>

## Last notes:

Customizing the functionality of this program is as easy as changing the first lines of the main() function, i.e., its flags:

```golang
func main() {
	urlflag := flag.String("url", "<your_url_string>", "the url we need to build a sitemap for")
	maxDepth := flag.Int("depth", <your_desired_depth_int>, "max depht of urls allowed")
    ...
```

Changing the text in between the <> marking will allow for you to make free use of the program. Make note of the secure protocols, for the program won't run correctly if you pàss http for an https website.

Output example using "https://gophercises.com" as the url, with 3 as maximum depth:

![image](https://user-images.githubusercontent.com/102031726/183408390-23a72797-fddb-42a9-86f1-2f90480019de.png)
