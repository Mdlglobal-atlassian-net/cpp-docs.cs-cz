---
title: Používání parametrů Lambda, objektů funkcí a omezených funkcí
ms.date: 11/04/2016
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
ms.openlocfilehash: 819605eac6408751456479fbc3daa38aac1418ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629395"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Používání parametrů Lambda, objektů funkcí a omezených funkcí

Kód jazyka C++ AMP, který chcete provést v akcelerátoru je zadán jako argument ve volání [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody. Jako tento argument můžete zadat výraz lambda nebo objekt funkce (funktoru). Kromě toho lambda výraz nebo objekt funkce může volat funkci s omezením jazyka C++ AMP. Toto téma používá algoritmus sčítání pole k předvedení výrazy lambda, objektů funkcí a omezených funkcí. Následující příklad ukazuje algoritmus bez kódu jazyka C++ AMP. Jsou vytvořeny dva 1rozměrné pole o stejné délce. Odpovídající celočíselné prvky jsou přidány a uloženy v třetí 1rozměrné pole. C++ AMP není používána.

```cpp
void CpuMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx <5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx <5; idx++)
    {
        std::cout <<sumCPP[idx] <<"\n";
    }
}
```

## <a name="lambda-expression"></a>Výraz lambda

Použití lambda výrazu je nejrychlejším způsobem použití jazyka C++ AMP pro přepsání kódu.

```cpp
void AddArraysWithLambda() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
             sum[idx] = a[idx] + b[idx];
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

Výraz lambda musí obsahovat jeden parametr indexování a musí obsahovat `restrict(amp)`. V tomto příkladu [array_view](../../parallel/amp/reference/array-view-class.md) `sum` objektu má pořadí 1. Parametr příkazu lambda je proto [index](../../parallel/amp/reference/index-class.md) objekt, který se má pořadí 1. Za běhu, výraz lambda je proveden jednou pro každý prvek [array_view](../../parallel/amp/reference/array-view-class.md) objektu. Další informace najdete v tématu [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).

## <a name="function-object"></a>Objekt Function

Akcelerátor kódu lze přetvořit na objekt funkce.

```cpp
class AdditionFunctionObject
{
public:
    AdditionFunctionObject(const array_view<int, 1>& a,
    const array_view<int, 1>& b,
    const array_view<int, 1>& sum)
    : a(a), b(b), sum(sum)
    {
    }

    void operator()(index<1> idx) restrict(amp)
    {
        sum[idx] = a[idx] + b[idx];
    }

private:
    array_view<int, 1> a;
    array_view<int, 1> b;
    array_view<int, 1> sum;
};

void AddArraysWithFunctionObject() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        AdditionFunctionObject(a, b, sum));

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

Objekt funkce musí obsahovat konstruktor a musí zahrnovat přetížení operátoru volání funkce. Operátor volání funkce musí obsahovat jeden parametr indexování. Instance objektu funkce je předána jako druhý argument [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody. V tomto příkladu tři [array_view](../../parallel/amp/reference/array-view-class.md) objekty jsou předány do konstruktoru objektů funkce. [Array_view](../../parallel/amp/reference/array-view-class.md) objekt `sum` má pořadí 1. Proto se parametr operátoru volání funkce je [index](../../parallel/amp/reference/index-class.md) objekt, který se má pořadí 1. Za běhu, funkce je spuštěna jednou pro každý prvek [array_view](../../parallel/amp/reference/array-view-class.md) objektu. Další informace najdete v tématu [volání funkce](../../cpp/function-call-cpp.md) a [objekty funkcí ve standardní knihovně C++](../../standard-library/function-objects-in-the-stl.md).

## <a name="c-amp-restricted-function"></a>Funkci s omezením AMP C++

Můžete přetvořit akcelerátor kódu vytvořením omezené funkce a jejím zavoláním z lambda výrazu nebo objektu funkce. Následující příklad kódu ukazuje, jak zavolat funkci s omezením z lambda výrazu.

```cpp
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)
{
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            AddElementsWithRestrictedFunction(idx, sum, a, b);
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

Funkce s omezením musí obsahovat `restrict(amp)` a souladu s omezeními popsanými v [omezení (C++ AMP)](../../cpp/restrict-cpp-amp.md).

## <a name="see-also"></a>Viz také

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe výrazů lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Volání funkcí](../../cpp/function-call-cpp.md)<br/>
[Objekty funkcí ve standardní knihovně C++](../../standard-library/function-objects-in-the-stl.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)