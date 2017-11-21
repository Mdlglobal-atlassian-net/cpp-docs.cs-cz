---
title: "Concurrency::fast_math – Namespace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: amp_math/Concurrency::fast_math
dev_langs: C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 14bdfdf5ab570567f78befd3c99bca5c56c5195e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math – obor názvů
Funkce `fast_math` obor názvů mít nižší přesnost, podporují pouze jednoduchou přesností (`float`) a volání vnitřní funkce DirectX. Existují dvě verze jednotlivé funkce, například `cos` a `cosf`. Obě verze přijmout a vrátit `float`, ale každý volá stejné DirectX vnitřní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[Cos](concurrency-fast-math-namespace-functions.md#cos)|Vypočítá Arkus kosinus argument|  
|[cosf –](concurrency-fast-math-namespace-functions.md#cosf)|Vypočítá Arkus kosinus argument|  
|[ASIN](concurrency-fast-math-namespace-functions.md#asin)|Vypočítá Arkus sinus argument|  
|[asinf –](concurrency-fast-math-namespace-functions.md#asinf)|Vypočítá Arkus sinus argument|  
|[Atan](concurrency-fast-math-namespace-functions.md#atan)|Vypočítá Arkus tangens argument|  
|[ATAN2](concurrency-fast-math-namespace-functions.md#atan2)|Vypočítá Arkus tangens _Y/_X|  
|[atan2f –](concurrency-fast-math-namespace-functions.md#atan2f)|Vypočítá Arkus tangens _Y/_X|  
|[atanf –](concurrency-fast-math-namespace-functions.md#atanf)|Vypočítá Arkus tangens argument|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Vypočítá se mezní hodnota argumentu|  
|[ceilf –](concurrency-fast-math-namespace-functions.md#ceilf)|Vypočítá se mezní hodnota argumentu|  
|[Cos](concurrency-fast-math-namespace-functions.md#cos)|Výpočet kosinu argument|  
|[cosf –](concurrency-fast-math-namespace-functions.md#cosf)|Výpočet kosinu argument|  
|[COSH](concurrency-fast-math-namespace-functions.md#cosh)|Vypočítá hodnotu hyperbolický kosinus argumentu|  
|[coshf –](concurrency-fast-math-namespace-functions.md#coshf)|Vypočítá hodnotu hyperbolický kosinus argumentu|  
|[Exp](concurrency-fast-math-namespace-functions.md#exp)|Vypočítá exponenciální argumentu základní e|  
|[exp2 –](concurrency-fast-math-namespace-functions.md#exp2)|Vypočítá exponenciální argumentu základní-2|  
|[exp2f –](concurrency-fast-math-namespace-functions.md#exp2f)|Vypočítá exponenciální argumentu základní-2|  
|[expf –](concurrency-fast-math-namespace-functions.md#expf)|Vypočítá exponenciální argumentu základní e|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|Vrátí absolutní hodnotu argumentu|  
|[fabsf –](concurrency-fast-math-namespace-functions.md#fabsf)|Vrátí absolutní hodnotu argumentu|  
|[Floor](concurrency-fast-math-namespace-functions.md#floor)|Vypočítá podlaží argumentu|  
|[floorf –](concurrency-fast-math-namespace-functions.md#floorf)|Vypočítá podlaží argumentu|  
|[Fmax](concurrency-fast-math-namespace-functions.md#fmax)|Určit maximální číselná hodnota, která jsou argumenty|  
|[fmaxf –](concurrency-fast-math-namespace-functions.md#fmaxf)|Určit maximální číselná hodnota, která jsou argumenty|  
|[Fmin](concurrency-fast-math-namespace-functions.md#fmin)|Určení minimální číselná hodnota z argumentů|  
|[fminf –](concurrency-fast-math-namespace-functions.md#fminf)|Určení minimální číselná hodnota z argumentů|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou|  
|[fmodf –](concurrency-fast-math-namespace-functions.md#fmodf)|Vypočítá zbytek _X/_Y s plovoucí desetinnou čárkou|  
|[frexp –](concurrency-fast-math-namespace-functions.md#frexp)|Získá mantisa a exponent _X|  
|[frexpf –](concurrency-fast-math-namespace-functions.md#frexpf)|Získá mantisa a exponent _X|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Určuje, zda argument má hodnotu konečné|  
|[isinf –](concurrency-fast-math-namespace-functions.md#isinf)|Určuje, zda je argument nekonečna|  
|[isNaN](concurrency-fast-math-namespace-functions.md#isnan)|Určuje, zda je argument NaN.|  
|[ldexp –](concurrency-fast-math-namespace-functions.md#ldexp)|Vypočítá reálné číslo z mantisa a exponent|  
|[ldexpf –](concurrency-fast-math-namespace-functions.md#ldexpf)|Vypočítá reálné číslo z mantisa a exponent|  
|[protokolu](concurrency-fast-math-namespace-functions.md#log)|Vypočítá základní e logaritmus argumentu|  
|[LOG10](concurrency-fast-math-namespace-functions.md#log10)|Vypočítá logaritmus o základu 10 argument|  
|[log10f –](concurrency-fast-math-namespace-functions.md#log10f)|Vypočítá logaritmus o základu 10 argument|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Vypočítá logaritmus o základu 2 argumentu|  
|[log2f –](concurrency-fast-math-namespace-functions.md#log2f)|Vypočítá logaritmus o základu 2 argumentu|  
|[logf –](concurrency-fast-math-namespace-functions.md#logf)|Vypočítá základní e logaritmus argumentu|  
|[modf –](concurrency-fast-math-namespace-functions.md#modf)|Rozdělí _X do zlomkové a částí celé číslo.|  
|[modff –](concurrency-fast-math-namespace-functions.md#modff)|Rozdělí _X do zlomkové a částí celé číslo.|  
|[Pow](concurrency-fast-math-namespace-functions.md#pow)|Vypočítá _X mocninu _Y|  
|[powf –](concurrency-fast-math-namespace-functions.md#powf)|Vypočítá _X mocninu _Y|  
|[Zaokrouhlit](concurrency-fast-math-namespace-functions.md#round)|Zaokrouhlí _X na nejbližší celé číslo|  
|[roundf –](concurrency-fast-math-namespace-functions.md#roundf)|Zaokrouhlí _X na nejbližší celé číslo|  
|[rsqrt –](concurrency-fast-math-namespace-functions.md#rsqrt)|Vrátí vzájemné druhé odmocniny argumentu|  
|[rsqrtf –](concurrency-fast-math-namespace-functions.md#rsqrtf)|Vrátí vzájemné druhé odmocniny argumentu|  
|[signbit –](concurrency-fast-math-namespace-functions.md#signbit)|Vrátí znaménko argumentu|  
|[signbitf –](concurrency-fast-math-namespace-functions.md#signbitf)|Vrátí znaménko argumentu|  
|[Sin](concurrency-fast-math-namespace-functions.md#sin)|Vypočítá hodnotu sinus argumentu|  
|[sincos –](concurrency-fast-math-namespace-functions.md#sincos)|Vypočítá sinus a kosinus hodnotu _X|  
|[sincosf –](concurrency-fast-math-namespace-functions.md#sincosf)|Vypočítá sinus a kosinus hodnotu _X|  
|[sinf –](concurrency-fast-math-namespace-functions.md#sinf)|Vypočítá hodnotu sinus argumentu|  
|[SINH](concurrency-fast-math-namespace-functions.md#sinh)|Vypočítá hodnotu hyperbolický sinus argumentu|  
|[sinhf –](concurrency-fast-math-namespace-functions.md#sinhf)|Vypočítá hodnotu hyperbolický sinus argumentu|  
|[Sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Vypočítá druhou odmocninu argumentu|  
|[sqrtf –](concurrency-fast-math-namespace-functions.md#sqrtf)|Vypočítá druhou odmocninu argumentu|  
|[Tan](concurrency-fast-math-namespace-functions.md#tan)|Vypočítá tečný hodnotu argumentu|  
|[tanf –](concurrency-fast-math-namespace-functions.md#tanf)|Vypočítá tečný hodnotu argumentu|  
|[TANH](concurrency-fast-math-namespace-functions.md#tanh)|Vypočítá hyperbolický tangens hodnotu argumentu|  
|[tanhf –](concurrency-fast-math-namespace-functions.md#tanhf)|Vypočítá hyperbolický tangens hodnotu argumentu|  
|[TRUNC](concurrency-fast-math-namespace-functions.md#trunc)|Zkrátí argument pro komponentu celé číslo|  
|[truncf –](concurrency-fast-math-namespace-functions.md#truncf)|Zkrátí argument pro komponentu celé číslo|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_math.h  
  
 **Namespace:** Concurrency::fast_math –  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
