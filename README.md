[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=12392779&assignment_repo_type=AssignmentRepo)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.


To start we need the recurrence relation, which should be 
T(n) = {1, if n $\leq 1; 3t(\frac{n}{3})+n^5,$ else. 
Using this we can turn this into an euation that looks like this

$ 3^iT(\frac{n}{3^i})+ \sum_{j=0}^{i-1} (3^j(\frac{n}{3^j})^5)$

We can set i to $ \log_3{n} $ and we can also take a $ n^5 $ out of the sumation, 
because it is in every equation and never changes, we can also ignore the sumation
becasue it is a constant

$ 3^{\log_3{n}}T(\frac{n}{3^{\log_3{n}}})+ n^5$

$ nT(1)+ n^5$

$ n+ n^5 \in O n^5$


