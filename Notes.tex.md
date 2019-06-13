# Symmetries for deep network architectures

Writing down our comments on deep network symmetries.


# Intuition for the "wide minima = good generalization" heuristic

This is one of the main intuitions offered as an explanation of generalization in deep nets, and I'd like to understand it better, since it's not immediately clear to me why it should hold. Also, I imagine it will enter into any story related to the kind of ensembling we're interested in. Would love to get others' insights...

Abusing some notation, let $\mathcal{L}(w_{opt}(\mathbf{train}))$ denote the training loss for the optimally trained weights $w_{opt}\in W$, where $W$ denotes the space of weights/parameters. I think the "wide minima heuristic" would be true *if* for every test set, we could always find some $w\in W$ in the vicinity of $w_{opt}$ (say $w\in B_r(w_{opt}) \subset W$ for a small radius $r$) such that

$$ \mathcal{L}(w(\mathbf{train})) = \mathcal{L}(w_{opt}(\mathbf{test})) $$

To be valid as a heuristic to learn about $\mathcal{L}$ I feel this needs to be true without any assumptions on $\mathcal{L}$, so that we actually need $w$ to satisfy

$$ w(\mathbf{train}) = w_{opt}(\mathbf{test}) ~~ (1) $$

I can "kind of" see why this might be true: e.g. if the data were normally distributed and we could assume that $ \mathbf{test} = \mathbf{train} + \mathbf{\epsilon}$ with $\mathbf{\epsilon}$ denoting a small normally distributed noise vector, and if...

Ok wait, stepping back: let $X$ and $Y$ denote the input and output spaces for our regression problem, and think of the functions $F = \text{Hom}(X, Y)$ as embedded in $X\times Y$, so we can think of our network architecture itself as a subset $\mathcal{A} \subset W \times (X \times Y)$. Therefore the tangent bundle $T\mathcal{A}$ is naturally embedded in $TW \oplus T(X\times Y) = TW \oplus TX \oplus TY$. Then we want to try to rewrite equation $(1)$ in terms of transversality of projections coming from $\pi_W$ and $\pi_X$, applied to $T\mathcal{A}$.

So $A)$ am I overthinking things or $B)$ would it be interesting to think carefully about what these conditions really look like when the data is complex (eg, natural images)?
