---
layout: post
title: "[React] Higher-Order Components 패턴 적용하기"
date: 2023-12-13 19:31:29 +0900
category: react
---

![banner](https://cdn.jsdelivr.net/gh/mulddang2/blog@main/public/img/high-order-components.png)

## 이슈

- UI에서 Todo가 없음에도, 전체완료 및 전체삭제가 보여집니다.

- 조건부 렌더링을 해도 되지만, 추가 로직이 생길 경우에 한 컴포넌트가 길어지고, 유지보수성이 떨어질 수 있다고 합니다. (참고: [화해기술블로그](https://blog.hwahae.co.kr/all/tech/11631){:target="\_blank"})

## 적용

따라서, 아래 코드와 같이 HOC(Higher-Order Components)를 사용해보았습니다.

- HOC는 '컴포넌트 로직 재사용'을 위한 패턴입니다.
- 상위에서 내용을 결정해서, 하위에 그 내용을 넘겨주는 방식으로 사용할 수 있습니다.

```javascript
function App() {
  const [text, setText] = useState('');
  const [todos, setTodos] = useState<TodoType[]>([]);

  const handleTextChange = (text: string) => {
    setText(text);
  };

  const handleSubmit = () => {};
  return (
    <main className='App'>
      // blabla~~~

      <TodoListArea todoCount={todos.length}>
        <TodoListTools />
        <Divider />
        <TodoList todos={todos} />
      </TodoListArea>
    </main>
  );
}

export default App;

```

TodoListArea 컴포넌트의 하위 children을 보여줄지, 말지를 할일목록의 갯수가 없으면 하위항목을 보여주지말자! 는 내용으로 적용해보았습니다.

```javascript
import { ReactNode } from "react";

interface TodoListAreaProps {
  children: ReactNode;
  todoCount: number;
}

// NOTE: HOC High order component
const TodoListArea = (props: TodoListAreaProps) => {
  if (props.todoCount < 1) return null;
  return <>{props.children}</>;
};

export default TodoListArea;
```

## 결과

- 아래와 같이 할일 목록이 없으므로, TodoListArea 컴포넌트에서 전체완료와 전체삭제를 보여주지 않게 됩니다.
  ![high-order-components 적용 이미지](https://velog.velcdn.com/images/js4072751/post/9457ef92-ced8-4f8e-8f84-092dc152f241/image.png)
