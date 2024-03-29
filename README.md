# iis-config-react-router
The configuration file required for IIS to make your react application responsive to all routes.

There's a Subdirectory branch that uses a bit different config file required for when deploying on subdirectories  (i.e your-app-url.com/subdirectory)

**Deployment Tips for React Application using react-router with Vite on IIS.**

Build your browser router with a basename if you're deploying on a subdirectory. 
Below example works for all kinds of routes, default & subdirectories.

```
const router = createBrowserRouter(
    createRoutesFromElements(
        <>
            <Route path='/' element={<RootLayout />} errorElement={<ErrorPage />} loader={RootLoader}>
                //Add your routes here
            </Route>
        </>
    ), { basename: `${import.meta.env.BASE_URL}`}
)
```

Build your project using `npx vite build`. 
If you deploy in a subdirectory, use `npx vite build --base=/yoursubdirectory`

Add the web.config file inside your IIS directory (Next to index.html). 

You should now be able to navigate to all your routes.
