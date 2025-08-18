
```java
class FixedSizedStack {
    private int maximumSize;
    private int[] arr;
    private int top;

    public FixedSizedStack(int size) {
        maximumSize = size;
        arr = new int[maximumSize];
        top = -1;
    }

    public boolean isEmpty() {
        return top == -1;
    }

    public boolean isFull() {
        return top == maximumSize-1;
    }

    public void push(int value) {
        if (isFull()) {
            throw new StackOverflowError(String.format("Stack is full. Maximum size is %d", maximumSize));
        }
        arr[++top] = value;
        System.out.printf("[Pushed into stack]: %d\n", value);
    }

    public int pop() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        return arr[top--];
    }

    public int peek() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        return arr[top];
    }

    @Override
    public String toString() {
        if (isEmpty()) {
            return "[empty stack]";
        }
        StringBuilder sb = new StringBuilder();
        for (int i = top; i >= 0; i--) {
            sb.append("| ").append(arr[i]).append(" |\n");
            if (i == top) {
                sb.append(" ^-- top\n");
            }
        }
        return sb.toString();
    }
}
```