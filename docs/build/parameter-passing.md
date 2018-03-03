---
title: "Předávání parametrů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0359a6cbbb1f646432b03722cdf4ba3010cffa72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="parameter-passing"></a>Předávání parametrů
První čtyři celočíselné argumenty jsou předány v registrech. Celočíselné hodnoty jsou předána (v pořadí zleva doprava) RCX, RDX, R8 a R9. Argumenty pět a vyšší se předávají v zásobníku. Všechny argumenty mají právo zarovnané v registrech. Důvodem je, pokud můžete volaného ignorovat horní bity registru musí být a k přístup jenom ta část registraci nezbytné.  
  
 Argumenty s plovoucí desetinnou čárkou a dvojitou přesností se předávají v XMM0 – XMM3 (až 4) se slotem celé číslo (RCX, RDX, R8 a R9), která se běžně používá pro tento základní slot právě ignorovány (viz příklad) a naopak.  
  
 [__m128](../cpp/m128.md) typy, pole a řetězců nejsou nikdy předávány okamžitou hodnotou, ale spíše je ukazatel předán do paměti přidělené volající. Struktury/sdružení o velikosti 8, 16, 32 nebo 64 bitů a __m64 jsou předávány, jako kdyby byly celá stejnou velikost. Struktury/sdružení než tyto velikosti jsou předány jako ukazatel paměti přidělené volající. Pro tyto typy předat jako ukazatel (včetně \__m128), volající přidělené dočasné paměti bude zarovnán na 16 bajtů.  
  
 Vnitřní funkce, které nepřidělujte místa v zásobníku a Nevolejte jiných funkcí můžete použít závislé registry předání argumentů další registrace, protože není úzkou vazbu mezi kompilátor a implementací vnitřní funkce. To je další možnost pro zlepšení výkonu.  
  
 Volaného má odpovědnost rozpětí parametry registru do prostoru jejich stínu v případě potřeby.  
  
 Následující tabulka shrnuje, jak jsou předávány parametry:  
  
|Typ parametru|Jak předaný|  
|--------------------|----------------|  
|Plovoucí desetinné čárky|První 4 parametry – XMM0 přes XMM3. Ostatní předány v zásobníku.|  
|Integer|První 4 parametry - RCX, RDX, R8 R9. Ostatní předány v zásobníku.|  
|Agregace (8, 16, 32 nebo 64 bitů) a __m64|První 4 parametry - RCX, RDX, R8 R9. Ostatní předány v zásobníku.|  
|Agregace (jiná)|Ukazatel. První 4 parametry předány jako ukazatel v RCX, RDX, R8 a R9|  
|__m128|Ukazatel. První 4 parametry předány jako ukazatel v RCX, RDX, R8 a R9|  
  
## <a name="example-of-argument-passing-1---all-integers"></a>Příklad argumentu předávání 1 – všechny celá čísla  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-2---all-floats"></a>Příklad 2 – všechny obtékaných objektů předávání argumentů  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Příklad argumentu předávání 3 – proměnné smíšený ints a obtékaných objektů  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Příklad argumentu předávání 4-__m64, \__m128 a agregace  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)