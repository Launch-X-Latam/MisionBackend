# Proyecto

## TODO APP

# Pendiente

Solo hice, cambie/cree los siguientes de un proyecto en blanco de React.js

App.js
```JavaScript
import './App.scss';
import Container from './components/Container'

function App() {
  return (
    <div className="App">
      <Container/>
    </div>
  );
}

export default App;

```

/components/Checkbox.jsx
```JavaScript
import React, { Fragment } from "react";

const Checkbox = props => {

    const {
        onChange,
        data: {id, description, done}
    } = props; 

    return (<Fragment>

        <svg viewBox="0 0 0 0" 
            style={{
                position: "absolute",
                zIndex: -1,
                opacity: 0
            }}>
            <defs>
                <path id="todo_line" d="M21 12.3h168v0.1z"/>
                <path id="todo_box" d="M21 12.7v5c0 1.3-1 2.3-2.3 2.3H8.3C7 20 6 19 6 17.7V7.3C6 6 7 5 8.3 5h10.4C20 5 21 6 21 7.3v5.4"/>
                <path id="todo_check" d="M10 13l2 2 5-5" />
                <circle id="todo_circle" cx="13.5" cy="12.5" r="10"/>
            </defs>
        </svg>

        <label className="todo new-item">
            <input
                className="todo_state"
                name={id}
                type="checkbox"
                defaultChecked={done}
                onChange={onChange}
            />

            <svg 
                xmlns="http://www.w3.org/2000/svg" 
                xmlnsXlink="http://www.w3.org/1999/xlink" 
                viewBox="0 0 200 25" 
                className="todo_icon">
                    <use xlinkHref="#todo_line"  className="todo_line" />
                    <use xlinkHref="#todo_box"  className="todo_box" />
                    <use xlinkHref="#todo_check"  className="todo_check" />
                    <use xlinkHref="#todo_circle"  className="todo_circle" />
            </svg>

            <div className="todo_text">{description}</div>
        </label>
    </Fragment>);
}

export default Checkbox;
```

/components/Container.jsx
```JavaScript
import React, { useState } from "react";
import FormTodo from './FormTodo';
import TaskList from './TaskList';

const Container = () => {
    const [list, setList] = useState([]);

    const addItem = addItem => {
        setList([...list, addItem])
    };

    return (
        <div>
            <FormTodo addItem={addItem}/>
            <TaskList list={list} setList={setList}/>
        </div>
    );
}

export default Container
```

/components/FormTodo.jsx
```JavaScript
import React, { useState } from "react";

const FormTodo = props => {
    const [description, setDescription] = useState("");
    const {addItem} = props;

    const handleSubmit = e =>  {
        e.preventDefault();
        console.log(description)
        
        addItem({
            done: false,
            id: (new Date()).toString(),
            description
        });

        setDescription("");
    }

    return (
        <form onSubmit={handleSubmit}>
            <div className="todo-list">
                <div className="file-input">
                    <input
                        type="text"
                        className="text"
                        value={description}
                        onChange={e => setDescription(e.target.value)}
                    />
                    <button
                        className="button pink"
                        disabled={description ? "" : "disabled"}
                    /*
                    Lo mismo:
                    if (Descripcion == "") {
                        disabled="disabled"
                    } else {
                        disabled=""
                    }
                    */
                    >
                        Agregar tarea
                    </button>
                </div>
            </div>
        </form>
    );
}

export default FormTodo;
```

/components/TaskList.jsx
```JavaScript
import React from "react";
import Checkbox from "./Checkbox";

const TaskList = props => {
    const {list, setList} = props;

    const onChangeStatus = e => {
        const {name, checked} = e.target;
        const updateList = list.map(item => ({
            ...item,
            done: item.id === name ? checked : item.done
        }));
        setList(updateList);
    };
    
    const onClickRemoveItem = e =>  {
        const updateList = list.filter(item => !item.done);
        setList(updateList)
    };

    const checkbox = list.map(item => (
        <Checkbox key={item.id} data={item} onChange={onChangeStatus} />
    ));

    return (
        <div className="todo-list">
            {list.length ? checkbox : "No hay tareas"}
            {list.length ? (
                <p>
                    <button className="button pink" onClick={onClickRemoveItem}> Delete</button>
                </p>
            ) : null}
        </div>
    )
}

export default TaskList;
```

```scss
html {
  background: #ddd;
  height: 100%;
  display: flex;
}
body {
  width: 100%;
  margin: auto;
}

.App {
  font-family: sans-serif;
  text-align: center;
}

.todo-list {
  background: #fff;
  font-size: 18px;
  max-width: 300px;
  margin: auto;
  margin-bottom: 24px;
  padding: 8px 16px;
  box-shadow: 0 5px 30px rgba(0,0,0,0.2);
}

$colorRosa: #C2185B;
$colorRosaHover: #E91E63;

$colorAzul: #1976D2;
$colorAzulHover: #03A9F4;

@mixin button($class, $color, $colorHover) {
  .button.#{$class}{background: $color;}
  .button.#{$class}:hover{background: $colorHover;}
  .button.#{$class}:active{background: $color;}
}

.button {
  outline: none;
  padding: 8px;
  border: 1px solid white;
  border-radius: 15px;
  color: white;
}

@include button ('pink', $colorRosa, $colorRosaHover);
@include button ('blue', $colorAzul, $colorAzulHover);

.file_input {
  padding: 2px;
  background: #f8f8f8;
}

.file_input > .text {
  outline: none;
  padding: 0px, 10px;
  font-size: 18px;
  width: 230px;
  height: 43;
  background: transparent;
  border: 0px solid;
}

$duracion: 0.4s;
$stroke: #34eb9f;
$colorText: #222222;
$colorTextChecked: #85e6e4;

.todo {
  display: block;
  position: relative;
  padding: 1em 1em 1em 16%;
  margin: 0 auto;
  cursor: pointer;
  border-bottom: solid 1px #ddd;
  &:last-child {border-bottom: none;}
}

.todo.new-item {
  opacity: 0;
  transform: translateX(100px);
  animation: fadeIn .3s linear forwards;
}

@keyframes fadeIn {
  to {
    transform: translateX(0px);
    opacity: 1;
  }
}

.todo_state {
  position: absolute;
  top: 0;
  left: 0;
  opacity: 0;
}

.todo_text {
  color: $colorText;
  text-align: right;
  transition: all $duracion/2 linear $duracion/2;
}

.todo_icon {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  width: 100%;
  height: auto;
  margin: auto;

  fill: none;
  stroke: $stroke;
  stroke-width: 2;
  stroke-linejoin: round;
  stroke-linecap: round;
}

.todo_line, .todo_box, .todo_check {
  transition: stroke-dashoffset $duracion cubic-bezier(0.075, 0.82, 0.165, 1)
}

.todo_circle {
  stroke: $stroke;
  stroke-dasharray: 1 6;
  stroke-width: 0;

  transform-origin: 13.5px 12.5px;
  transform: scale(0.4) rotate(0deg);
  animation: none $duracion linear;

  @keyframes explode {
    30% {
      stroke-width: 3;
      stroke-opacity: 1;
      transform: scale(0.8) rotate(40deg);
    }

    100% {
      stroke-width: 0;
      stroke-opacity: 0;
      transform: scale(1.1) rotate(60deg);
    }
  }

}

.todo_box {
  stroke-dasharray: 56, 56;
  stroke-dashoffset: 0;
  transition-delay: $duracion * 0.2;
}

.todo_check {
  stroke: $stroke;
  stroke-dasharray: 9.8 9.8;
  stroke-dashoffset: 9;
  transition-delay: $duracion * 0.4;
}

.todo_line {
  stroke-dasharray: 168, 168;
  stroke-dashoffset: 168;
}

.todo_circle {
  animation-delay: $duracion * 0.7;
  animation-duration: $duracion * 0.7;
}

.todo_state:checked {
  ~ .todo_text { transition-delay: 0s; color: $colorTextChecked; opacity: 0.6;}
  ~ .todo_icon .todo_box { stroke-dashoffset: 56; transition-delay: 0s; }
  ~ .todo_icon .todo_line { stroke-dashoffset: -8; }
  ~  .todo_icon .todo_check { stroke-dashoffset: 0; transition-delay: $duracion * 0.6; }
  ~ .todo_icon .todo_circle { animation-name: explode;}
}
```

---

[*Volver* **&ldca;**](/README.md "Menu principal") 
[*Subir* **&#11165;**](# "Ir al título")