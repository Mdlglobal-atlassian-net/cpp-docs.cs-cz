---
title: "Pomocí Lambdas, objektů funkcí a omezených funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afec84ba6e3c007e576c37b4a7afc71fe62691ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Používání parametrů Lambda, objektů funkcí a omezených funkcí
C++ AMP kód, který chcete spustit na akcelerátor je zadaný jako argument při volání [parallel_for_each –](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metoda. Výraz lambda nebo objekt funkce (functor) můžete zadat jako tento argument. Kromě toho můžete objekt funkce nebo výraz lambda volání funkce C++ AMP omezený. Toto téma používá nepodporovaný algoritmus přidání pole k předvedení lambdas, objektů funkcí a omezených funkcí. Následující příklad ukazuje, že algoritmus bez kódu C++ AMP. Jsou vytvořeny dva 1jednorozměrná pole stejné délky. Odpovídající elementy celé číslo se přidat a uložená v třetí dimenzí 1 pole. C++ AMP se nepoužije.  
  
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
 Pomocí výrazu lambda je velmi přímočarou způsob, jak používat C++ AMP přepište kód.  
  
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
  
 Výraz lambda musí obsahovat jeden parametr indexování a musí obsahovat `restrict(amp)`. V příkladu [array_view](../../parallel/amp/reference/array-view-class.md) `sum` objekt má pořadí 1. Proto je parametr k příkazu lambda [index](../../parallel/amp/reference/index-class.md) objekt, který má pořadí 1. V době běhu je jednou provést výrazu lambda pro každý prvek v [array_view](../../parallel/amp/reference/array-view-class.md) objektu. Další informace najdete v tématu [syntaxe výrazu Lambda](../../cpp/lambda-expression-syntax.md).  
  
## <a name="function-object"></a>Objekt Function  
 Kód akcelerátoru můžete dvoufaktorového do objektu funkce.  
  
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

 Objekt funkce musí obsahovat konstruktor a musí obsahovat přetížení operátor volání funkce. Operátor volání funkce musí obsahovat jeden parametr indexování. Instance objektu funkce se předá jako druhý argument [parallel_for_each –](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metoda. V tomto příkladu tři [array_view](../../parallel/amp/reference/array-view-class.md) předávání objektů do konstruktoru objektu funkce. [Array_view](../../parallel/amp/reference/array-view-class.md) objekt `sum` má pořadí 1. Proto parametr operátor volání funkce je [index](../../parallel/amp/reference/index-class.md) objekt, který má pořadí 1. V době běhu funkce je spuštěna jednou pro každý prvek ve [array_view](../../parallel/amp/reference/array-view-class.md) objektu. Další informace najdete v tématu [volání funkce](../../cpp/function-call-cpp.md) a [funkce objekty ve standardní knihovně C++](../../standard-library/function-objects-in-the-stl.md).  
  
## <a name="c-amp-restricted-function"></a>C++ AMP omezené funkce  
 Kód akcelerátoru můžete další faktor vytvořením omezené funkce a volání z výrazu lambda nebo objekt funkce. Následující příklad kódu ukazuje, jak volat funkci s omezeným přístupem z výrazu lambda.  
  
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
  
 Musí obsahovat funkci s omezeným přístupem `restrict(amp)` a souladu s omezeními, které jsou popsány v [omezení (C++ AMP)](../../cpp/restrict-cpp-amp.md).  
  
## <a name="see-also"></a>Viz také  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Syntaxe výrazu lambda](../../cpp/lambda-expression-syntax.md)   
 [Volání funkce](../../cpp/function-call-cpp.md)   
 [Objekty funkcí ve standardní knihovně C++](../../standard-library/function-objects-in-the-stl.md)   
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

