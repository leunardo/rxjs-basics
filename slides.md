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

> Observables are **lazy** Push collections of multiple values

```js
const observable = new Observable(subscriber => {
    subscriber.next(1);
    subscriber.next(1);
    subscriber.next(1);
    subscriber.complete();
});
```

--

### Observer

--

### Subscription

--

### Subject

---

### Função *pipe*

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