# Svelte Practice

Svelte is a tool for building `fast web applications`.

Similar to React and Vue, but there's a crucial difference:

- Svelte converts your app into `ideal Javascript` at build time, rather than interpreting your application code at run time.
- So, you don't pay the performance cost of the framework's abstractions.
- And you don't incur a penalty when your app first loads.

## Understanding Svelte's components

In Svelte, an application is composed from one or more components. (Similar to React && Vue, repeatedly.)
A component is a reusable self-contained block of code that `encapsulates HTML, CSS and JS` that belong together, written into a `.svelte` file.

## Svelte의 특징

- write less code (보다 적은 코드로)
- no virtual dom (가상 돔 없이)
- Truly reactive (진정한 반응형)

### Write less code

코드 작성에 있어 셋 중 가장 직접적으로 와닿는 부분은 `write less code` 일 것입니다. state를 정의하는 부분을 React, Vue와 비교해 보겠습니다.

```js
// Svelte
let a = 1;
let b = 2;

// React
export default () => {
    const [a, setA] = useState(1);
    const [b, setB] = useState(2);
}

// Vue
export default {
    data: function () {
        return {
            a: 1,
            b: 2,
        }
    }
}
```

적은 양의 코드로 같은 결과를 낸다면, 생산성에서 큰 차이가 날 것은 당연합니다. 

### Truly reactive

```vue
<script>
let count = 0
$: doubled = count * 2

$: if(count >= 10) {
	alert('카운트가 10을 넘었습니다. ')
	count = 9
}

$: {
	console.log( count )
	console.log( doubled )
}

function handleClick() {
    // calling this function will trigger an
    // update if the markup references `count`
	count += 1
}

</script>

<button on:click={handleClick}>
	클릭수 { count } {count === 1 ? 'time' : 'times'}
</button>

<p>{count} 두배는 {doubled} <p/>
```

간단한 코드 몇줄로 button tag에 event binding, 그에 따른 state의 변경, 변경에 따른 alert, console의 출력 등 다양한 기능이 작동하는 것을 볼 수 있습니다.

### $: marks a statement as reactive



또 하나의 특징으로 svelte는 빌드 시에 svelte 소스는 최소한으로 하고, 순수한 JS 형태로 컴파일됩니다. 따라서 빌드 결과물의 사이즈도 작고, 당연히 사용되는 메모리도 적습니다.
