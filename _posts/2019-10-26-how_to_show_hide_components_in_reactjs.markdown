---
layout: post
title:      "How to show/hide components in ReactJS"
date:       2019-10-26 16:14:45 +0000
permalink:  how_to_show_hide_components_in_reactjs
---

Adding a show/hide functionality to a React component it not very complicated and it’s a neat  way to make your app dynamic and organized.
This is why I wanted to add this functionality to my React app.
My app is called You-Got-This and its a goal tracker. 
You-Got-This has an `EventInput` component which contains two child components:  `DateTimePicker` and `AddToCalendar`. These are built in components from the `react-datetime-picker` and `react-add-to-calendar` packages, which I imported. Implementing these packages allows users to pick a date and time for an event and gives them the option to add the event to their calendar (google, yahoo).

So the first step is to add a new property to the component’s state that checks if we are currently rendering the `DateTimePicker` and `AddToCalendar` components to the DOM. In other words, are the date-time picker and add-to-calendar button visible on the web page or not? 

In my code, I called this property `showPicker` and set it to `false` so the date-time picker and add-to-calendar button will not show when the page is initially rendered:

```
state={
        date: new Date(),
        event: {
            title: this.props.step.text,
            description: '',
            location: '',
            startTime: new Date(),
            endTime: new Date()
          },
        showPicker : false
    }
```

The second step is to add a button with an `onClick` event listener that when clicked will call the `handleShowPicker` function:


```
<button className="btn btn-link btn-lg" onClick={()=> this.handleShowPicker()}>Add an Event</button>
```

The `handleShowPicker` function changes the showPicker value in the state, it toggles between `true` and `false` on each click on the  `Add an Event` button:

```
handleShowPicker(){
      this.setState({showPicker: !this.state.showPicker})
    }
```

Here, we are setting the state to the opposite value of the current state, so if the current showPicker state is false, a click on `Add an Event` will change the state to true, and vise versa. 

Next we should use the current state value of the `showPicker` property to determine whether the `DateTimePicke` and `AddToCalendar` components should be rendered or not. For this I used the ternary operator: 

```
render() {
        let icon = { 'calendar-plus-o': 'left' };
        return (
          <div>
            <button className="btn btn-link btn-lg" onClick={()=> this.handleShowPicker()}>Add an Event</button>
            {this.state.showPicker ? 
            <form onSubmit={event => this.handleSubmit(event)}>
              <DateTimePicker
                onChange={this.onChange}
                value={this.state.date}
               />
              <AddToCalendar 
                event={this.state.event}
                buttonTemplate={icon}
                />
               <input type="submit" value="submit"/>
            </form>
              : null
             }
          </div>
        )
    }
```
If `this.state.showPicker` is set to true, then render the child components, else, return `null`.
This will toggle between showing the date-time picker and the add-to-calendar button and hiding them. 






