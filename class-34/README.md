# `<Auth />`

Today, we will combine Authentication (valid user is logged in) and Authorization (what permissions does the user have) to create a UI that ensures that users only have access to content and functionality that they're granted access to.

## Learning Objectives

### Students will be able to

#### Describe and Define

- Role based access control
- Fetch and Superagent `Authorization` Headers

#### Execute

- Create a rules based application
- Authorize using both "Basic Authorization" and a "Bearer Token"
- Hide and Show components, links, pages based on both login status and permissions

## Today's Outline

<!-- To Be Completed By Instructor -->

## Notes

### Implementing RBAC with Conditional Rendering

What problems do we need to solve for?

- Is this a valid user (are they logged in)?
- What is the user authorized to do?
  - Which parts of our application care about this?
  - How can we determine this?
    - What's in the token?
    - Contact between the UI and the API
- How do we make this easy to use?

### Proposal

#### `Authorization` Context

- User State
- Methods
  - `can()` (for authorization)

#### `<Auth />` component

- Based on your permissions and login status, it either gives you access to a component or jsx or hides it.
- When you are authenticated, `props.children` renders, otherwise, null
- With a capability prop ... if you are authenticated AND have the right permissions, `props.children` renders, otherwise, null
- Can another conditional rendering component help us within the `<Auth />` component?

```javascript
// The div only shows if you are logged in
  <Auth>
    <div />
  </Auth>

// The div only shows if you are logged in AND have read permissions
  <Auth capability="read">
    <div />
  </Auth>
```
