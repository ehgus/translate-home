---
layout: default
title:  The Julia Language
---
<link rel="canonical" href="http://julialang.org">

<!--<div style="display: flex; flex-direction: row; align-items:center; margin-bottom: 32px">
    <div style="width: 48%; text-align: center">
        <div style="justify-content:center; margin-bottom: 16px; display: flex; flex-direction: row; align-items:center">
            <a href="http://juliacon.org"><img src="/images/juliacon2017.svg" style="width:200px; height: auto"></a>
            <div style="margin-left: 16px; margin-top: 16px; font-weight: bold; font-size: 2.5em">2017</div>
        </div>
        <div>
            June 20th - June 24th 2017, Berkeley, CA. <br>
            <a href="http://juliacon.org/2017/schedule">Talks and workshops.</a>
            <a href="https://www.eventbrite.com/e/juliacon-2017-tickets-31531297961?ref=ebtnebtckt">Tickets.</a>
        </div>
    </div>
    <div style="width: 48%; text-align: center">
        <div style="justify-content:center; margin-bottom: 16px; display: flex; flex-direction: row; align-items:center">
            <a href="/soc/ideas-page.html"><img src="/images/juliasock.png" style="width:88px; height: auto"></a>
        </div>
        <div>
            Julia is part of <b><a href="https://summerofcode.withgoogle.com/">Google Summer of Code 2017</a>!</b><br>
            Students are working on these <a href="https://summerofcode.withgoogle.com/organizations/5642180010967040/">18 projects</a>.
        </div>
    </div>
</div>-->

[줄리아](http://julialang.org)는 수치 컴퓨팅(numerical computing)을 다루는 고급(high-level), 고성능의 동적 프로그래밍 언어입니다.
세련된 컴파일러, [분산 병렬 실행](/ko/manual/parallel-computing), 정밀한 수치 표현, 그리고 [방대한 수학 함수 라이브러리](/ko/#Standard-Library-1)를 만나보세요.
 줄리아의 기반(Base) 라이브러리는 대부분 줄리아로 작성되었으며, [선형 대수](/ko/stdlib/linalg), [난수 생성](/ko/stdlib/numbers#Random-Numbers-1), [신호 처리](https://github.com/JuliaDSP/DSP.jl), 그리고 [문자열 처리](/ko/stdlib/strings#lib-strings-1)를 위해 C와 포트란으로 작성된 고품질의 오픈소스 라이브러리들을 통합하였습니다.
아울러 줄리아 개발 커뮤니티는 다양한 [외부 패키지들](http://pkg.julialang.org)을 작업하며 활기차게 기여하고 있습니다. [IJulia](https://github.com/JuliaLang/IJulia.jl)는 [주피터 프로젝트(Jupyter)](http://jupyter.org)와 줄리아 커뮤니티의 공동 작업으로, 브라우저에서 줄리아를 실행, 편집하는 그래픽 노트북 인터페이스를 제공합니다.

<!--
This keynote talk by Stefan Karpinski at [ODSC Boston](https://www.odsc.com/boston) (2016) on [the two language problem](https://www.youtube.com/watch?v=B9moDuSYzGo) explains much of the motivation behind Julia:

<div style="text-align: center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/B9moDuSYzGo" frameborder="0" allowfullscreen></iframe>
</div>
-->

Julia programs are organized around [multiple dispatch](http://docs.julialang.org/en/stable/manual/methods/#man-methods); by defining functions and overloading them for different combinations of argument types, which can also be user-defined.
For a more in-depth discussion of the rationale and advantages of Julia over other systems, see the following highlights or read the [introduction](http://docs.julialang.org/en/stable/manual/introduction/) in the [online manual](http://docs.julialang.org).


JuliaCon 2017, the annual conference on Julia was held from June 20th to June 24th at the University of California, Berkeley. Below is a random video from our youtube playlist of the talks. Click on the playlist icon to check out the other videos.

{% include juliacon-player-2017.html %}

# A Summary of Features

* [Multiple dispatch](http://en.wikipedia.org/wiki/Multiple_dispatch): providing ability to define function behavior across many combinations of argument types
* Dynamic type system: types for documentation, optimization, and dispatch
* Good performance, approaching that of statically-compiled languages like C
* Built-in package manager
* [Lisp-like macros](http://docs.julialang.org/en/stable/manual/metaprogramming/#macros) and other [metaprogramming facilities](http://docs.julialang.org/en/stable/manual/metaprogramming/)
* Call Python functions: use the [PyCall](https://github.com/stevengj/PyCall.jl) package
* [Call C functions](http://docs.julialang.org/en/stable/manual/calling-c-and-fortran-code/) directly: no wrappers or special APIs
* Powerful shell-like capabilities for [managing other processes](http://docs.julialang.org/en/stable/manual/running-external-programs/)
* Designed for [parallelism and distributed computation](http://docs.julialang.org/en/stable/manual/parallel-computing/)
* [Coroutines](http://en.wikipedia.org/wiki/Coroutine): lightweight "green" threading
* [User-defined types](http://docs.julialang.org/en/stable/manual/types/) are as fast and compact as built-ins
* Automatic generation of efficient, specialized code for different argument types
* Elegant and extensible [conversions and promotions](http://docs.julialang.org/en/stable/manual/conversion-and-promotion/) for numeric and other types
* Efficient support for [Unicode](http://en.wikipedia.org/wiki/Unicode), including but not limited to [UTF-8](http://en.wikipedia.org/wiki/UTF-8)
* [MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md): free and open source

# High-Performance JIT Compiler

Julia's LLVM-based just-in-time (JIT) compiler combined with the language's design allow it to approach and often match the performance of C.
To get a sense of relative performance of Julia compared to other languages that can or could be used for numerical and scientific computing, we've written a small set of micro-benchmarks in a variety of languages:
[C](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.c),
[Fortran](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.f90),
[Julia](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.jl),
[Python](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.py),
[Matlab/Octave](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.m),
[R](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.R),
[JavaScript](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.js),
[Java](https://github.com/JuliaLang/julia/tree/master/test/perf/micro/java/src/main/java),
[Lua](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.lua),
[Mathematica](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.nb).
We encourage you to skim the code to get a sense for how easy or difficult numerical programming in each language is.

<center>
<div class="figure" style="align: center; width: 77%">
{% include benchmarks.svg %}
<p class="caption"><b>Figure:</b>
Benchmark times relative to C (smaller is better, C performance = 1.0). Plot created with
<a href="https://github.com/dcjones/Gadfly.jl">Gadfly</a> and
<a href="https://github.com/JuliaLang/IJulia.jl">IJulia</a> from
<a href="http://nbviewer.ipython.org/url/julialang.org/benchmarks/benchmarks.ipynb">this notebook</a>.
See the <a href="/benchmarks/">benchmarks page</a> for more information.
</p>

</div>
</center>

# A quick taste of Julia

To give a quick taste of what Julia looks like, here is the code used in the Mandelbrot and random matrix statistics benchmarks:

{% highlight julia %}
function mandel(z)
    c = z
    maxiter = 80
    for n = 1:maxiter
        if abs2(z) > 4
            return n-1
        end
        z = z^2 + c
    end
    return maxiter
end

function randmatstat(t)
    n = 5
    v = zeros(t)
    w = zeros(t)
    for i = 1:t
        a = randn(n,n)
        b = randn(n,n)
        c = randn(n,n)
        d = randn(n,n)
        P = [a b c d]
        Q = [a b; c d]
        v[i] = trace((P.'*P)^4)
        w[i] = trace((Q.'*Q)^4)
    end
    std(v)/mean(v), std(w)/mean(w)
end
{% endhighlight %}

The code above is quite clear, and should feel familiar to anyone who
has programmed in other mathematical languages.  The Julia
implementation of `randmatstat` is considerably simpler than the
equivalent [C
implementation](https://github.com/JuliaLang/julia/blob/master/test/perf/micro/perf.c#L126),
without giving up much performance. Planned compiler optimizations
will close this performance gap in the future.  By design, Julia
allows you to range from tight low-level loops, up to a high-level
programming style, while sacrificing some performance, but gaining the
ability to express complex algorithms easily. This continuous spectrum
of programming levels is a hallmark of the Julia approach to
programming and is very much an intentional feature of the language.

# Designed for Parallelism and Cloud Computing

Julia does not impose any particular style of parallelism on the user.
Instead, it provides a number of [key building blocks for distributed computation](http://docs.julialang.org/en/stable/manual/parallel-computing), making it flexible enough to support a number of styles of parallelism, and allowing users to add more.
The following simple example demonstrates how to count the number of heads in a large number of coin tosses in parallel.

{% highlight julia %}
nheads = @parallel (+) for i=1:100000000
  rand(Bool)
end
{% endhighlight %}

This computation is automatically distributed across all available compute nodes, and the result, reduced by summation (`+`), is returned at the calling node.

Here is a screenshot of a web-based interactive [IJulia Notebook](https://github.com/JuliaLang/IJulia.jl) session, using [Gadfly](https://github.com/dcjones/Gadfly.jl). [JuliaBox](http://www.juliabox.com) provides a way to run IJulia notebooks in your browser on Docker sandboxed containers provisioned on demand.

<a href="/images/ijulia.png" target="_blank"><img class="u-center" src="/images/ijulia.png" width="90%" /></a>

This paves the way for fully cloud-based operation, including data management, code editing and sharing, execution, debugging, collaboration, analysis, data exploration, and visualization.
The eventual goal is to let people stop worrying about administering machines and managing data and get straight to the real problem.

[Gadfly](https://github.com/GiovineItalia/Gadfly.jl) can produce various plots with various rendering backends in the browser (SVG, PDF, PNG and various other backends are also supported). Interactivity can be added to graphs and plots with the [Interact.jl](https://github.com/JuliaGizmos/Interact.jl) package. A small sampling of the capabilities of Gadfly is presented below.

<a href="/images/gadfly-demo.png" target="_blank"><img src="/images/gadfly-demo.png" width="100%" /></a>

# Free, Open Source and Library-Friendly

The core of the Julia implementation is licensed under the [MIT license](http://en.wikipedia.org/wiki/MIT_License).
Various libraries used by the Julia environment include their own licenses such as the [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License), [LGPL](http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License), and [BSD](http://en.wikipedia.org/wiki/BSD_licenses)
(therefore the environment, which consists of the language, user interfaces, and libraries, is under the GPL).
The language can be built as a shared library, so users can combine Julia with their own C/Fortran code or proprietary third-party libraries.
Furthermore, Julia makes it [simple to call external functions](http://docs.julialang.org/en/stable/manual/calling-c-and-fortran-code/) in C and Fortran shared libraries, without writing any wrapper code or even recompiling existing code.
You can try calling external library functions directly from Julia's interactive prompt, getting immediate feedback.
See [LICENSE](https://github.com/JuliaLang/julia/blob/master/LICENSE.md) for the full terms of Julia's licensing.