## what is different between combination and permutation?

>[reference](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)

* when the order does matter, it is a permutation.
* when the order does not matter, it is a combination.

### Permutation

**1. Repetition is allowed:**

Such as a permutation lock,  the number is '333'.

For example, choose 3 of those things(n), the permutations are: 
```
n*n*n
```

**2. No repetition:**

For example the three first people in a running race, you can't be first and second, assume there are five people, the permutations are:
```
5*4*3

!5 / !(5-3)

choose r from n:
!n / !(n-r)
```
### Combination

**1. Repetition is allowed**

```
There are five flavors of ice cream: banana, chocolate, lemon, strawberry, vanilla.

We have three scoops, how many variations will there be?

let's use letters for the flavors: {b, c, l, s, v}. Examples selections include:

1. {c,c,c} {three scoops chocolate}
 >ooo>>>
2. {b,l,v} (one each of banana, lemon, vanilla)
 o>>o>>o
3. {b,v,v} (one scoop of banana, two scoop of vanilla)
 o>>>>o

!n / !r * !(n - r)

!(3 + 5 - 1) / !3 * !(5 - 1)

!(r + n - 1) / !r * !((r + n - 1) - r) = !(r + n - 1) / !r * !(n - 1)

```

**2.No repetition** 

```
choose 3 from 3

the permutations are:
123
132
213
231
312
321

the combinations are:
123

3! / !(3-3)*!3

choose r from n:

n! / !(n-r)*!r

```