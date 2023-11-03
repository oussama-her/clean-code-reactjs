# clean-code-reactjs

### jwt verification logic

**Bad:**

```javascript
const PrivateRoute = ({ component: Component, ...rest }) => (
    <Route {...rest} render={props => (
        hasJWT() ? <Component {...props} /> : <Redirect to="/login" />      👎️
        )}/>
);

return <PrivateRoute />;
```

**Good:**

```javascript

const renderComponent = (props, Component) => {
    return hasJWT() ? <Component {...props} /> : <Redirect to="/login" />;
};

const PrivateRoute = ({ component: Component, ...rest }) => (                       👍️
	  <Route {...rest} render={props => renderComponent(props, Component)} />
);

return <PrivateRoute />;
```
