## Application demo

The purpose of this page is to demonstrate the functionality of the application that was deployed on local k3d cluster using ArgoCD.

### Steps

1. Expose application via port-forwarding -> `kubectl port-forward -n demo svc/ambassador 8088:80`
2. Open terminal in spearate window and first check if app is accessible: 
`curl localhost:8088`
You should see the app version as an output.
3. The applicaction converts the `.png` files into `ASCII art`. Lets check if appliaction works as expected by downloading some picture and use application to convert it to the ASCII.
```
curl -F 'image=@<image_path>' localhost:8088/img/
```
### Demonstration
![ascii_demo](../blob/gifs/ascii_art_demo.gif)