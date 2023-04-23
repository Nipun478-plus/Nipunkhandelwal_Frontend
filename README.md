# STEELEYE-LIMITED-Assignment






Ques:- Explain what the simple LIST component does?
Ans:- The LIST component is a React component that displays a list of items. Considering the given code, Single ListItem and WrappedList are two of the child components. The SingleListItem is responsible for the rendering of a single item of the list, while the WrappedListComponent is responsible for rendering the entire list. The WrappedListComponent component maps over the list of items and renders a SingleListItem component for each item.




Ques:- What Problems / Warnings are there with the code?
* First Problem I facing 
The setSelectedIndex function is not defined correctly. It should be defined using useState hook. It can be defined like:
const[selectedIndex, setSelectedIndex]=useState(null);
* Second Probelem I Facing
The isSelected prop in the SingleListItem component is not being passed correctly. It can be corrected by: isSelected={selectedIndex === index}
* third and last
The PropTypes for the items prop in the WrappedListComponent component are not defined correctly. It should be defined like: PropTypes.arrayOf{PropTypes.shape({text: PropTypes.string.isRequired}))




Ques:- Please fix, optimize, and/or modify the component as much as you think is necessary.
Ans:- Ans of optimiized code is given in src file there i make code more optimize 
