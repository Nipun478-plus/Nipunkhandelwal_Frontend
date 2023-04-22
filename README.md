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
Ans:- So here is optimize version of the code :-

import React, { useState, useEffect, useCallback } from 'react';
import PropTypes from 'prop-types';

// Single List Item
const SingleListItem = ({
index,
isSelected,
onClickHandler,
text,
}) => {
return (
<li
style={{ backgroundColor: isSelected === index ? 'green' : 'red'}}
onClick={() => onClickHandler(index)}
>
{text}
</li>
);
};

SingleListItem.propTypes = {
index: PropTypes.number.isRequired,
isSelected: PropTypes.number,
onClickHandler: PropTypes.func.isRequired,
text: PropTypes.string.isRequired,
};

// List Component
const List = ({ items }) => {
const [selectedIndex, setSelectedIndex] = useState(null);

useEffect(() => {
setSelectedIndex(null);
}, [items]);

const handleClick = useCallback(
(index) => {
setSelectedIndex(index);
},
[setSelectedIndex]
);

return (
<ul style={{ textAlign: 'left' }}>
{items.map((item, index) => (
<SingleListItem
key={index}
{...item}
onClickHandler={handleClick}
index={index}
isSelected={selectedIndex}
/>
))}
</ul>
)
};

List.propTypes = {
items: PropTypes.arrayOf(PropTypes.shape({
text: PropTypes.string.isRequired,
})),
};

List.defaultProps = {
items: null,
};

export default List;

