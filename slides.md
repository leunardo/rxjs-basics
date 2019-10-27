---
theme : "blood"
transition: "slide"
highlightTheme: "tomorrow-night"
logoImg: "https://raw.githubusercontent.com/ReactiveX/rxjs-docs/master/src/favicon.ico"
slideNumber: false
title: "RxJS Basics"
---

### O que é programação reativa?

<span class="fragment">
    Programação reativa é programar com fluxos(streams) de dados assíncronos.
</span>

--

#### Pilares da programação reativa

<span class="fragment">
    <li>Elástico: Reage à demanda/carga: aplicações podem 
    fazer uso de múltiplos núcleos e múltiplos servidores</li>
</span>
<span class="fragment">
    <li>Resiliente: Reage às falhas; aplicações reagem
     e se recuperam de falhas de software, hardware e de conectividade;</li>
</span>


--

#### Pilares da programação reativa

<span class="fragment">
    <li>Message Driven: Reage aos eventos (event driven): em vez de compor
     aplicações por múltiplas threads síncronas, sistemas são compostos de
     gerenciadores de eventos assíncronos e não bloqueantes;</li>
</span>
<span class="fragment">
    <li>Responsivo: Reage aos usuários: aplicações que oferecem interações 
     ricas e “tempo real” com usuários.</li>
</span>

---

### O que é RxJS?
#### Reactive Extensions Library for JavaScript

<span class="fragment">
    RxJS é uma biblioteca para programação reativa utilizando o pattern <em>Observer</em>
</span>

--

<img src="https://upload.wikimedia.org/wikipedia/commons/8/8d/Observer.svg" style="width: 100%"></img>

---

### Conceitos fundamentais

--

#### Observable

> Observables são **lazy** push collections de múltiplos valores

```js
const observable = new Observable(observer => {
    observer.next(1);
    observer.next(2);
    observer.next(3);
    observer.complete();
});
```

--

### Subscription

> A Subscription é um objeto que representa um recurso descartável, que geralmente é resultado da execução de um Observable.

```js
const subscription = observable.subscribe({
    next: (x) => console.log(x)
});

subscription.unsubscribe();
```

--

### Subject

> O Subject é um tipo especial de Observable que permite que o seu valor seja compartilhado com diversos Observers

Todo Subject é um `Observable` e um `Observer`. Isso nos dá acessos aos métodos:

- observable
   - subscribe
- observer
   - next
   - complete
   - error

--

### Subject

```js
const subject = new Subject<number>();
const logOnNext = (observerName) => ({
    next: (v) => console.log(`${observerName}: ${v}`)
});

subject.subscribe(logOnNext('observerA'));
subject.subscribe(logOnNext('observerB'));
 
subject.next(1);
subject.next(2);

// Logs:
// observerA: 1
// observerB: 1
// observerA: 2
// observerB: 2
```

---

### Behavior Subject
#### Um tipo especial de Subject

>  Armazena o último valor emitido para os seus Observers, and sempre que algum novo Observer se inscreve, ele imediatamente recebe o valor atual do BehaviorSubject.

Pode ser utilizado como uma técnica de gerenciamento de estado, combinando com o operador `scan`.

---

### Behavior Subject

```js
const todoList = new BehaviorSubject([]);
todoList.value // [];

todoList.subscribe({
    next: (todos) => console.log('I have left: ' + todos)
});
// I have left: []

todoList.next(['homework']);
// I have left ['homework']
```

---

### Função *pipe*

A função `pipe` está no Observable e permite que seja utilizado o `pipeline pattern` para a transformação do valor emitido dentro do Observable.

Exemplo utilizando `pipe` com o operador `map`:
```js
const observable = new Observable(observer => {
    observer.next(10);
    observer.complete();
});

observable
    .pipe(map(value => value * value))
    .subscribe(value => console.log(value));
// 100
```

---

### Operadores

---

### Conceitos avançados

--

### Scheduler

---

### Marble Sintax


---

### Criando testes unitários usando a marble sintax