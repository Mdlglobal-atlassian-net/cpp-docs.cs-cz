---
title: noexcept (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noexcept_cpp
dev_langs: C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5068c7cf010c128fd7954ddfd356f49158bf6f17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** Určuje, zda funkce může vyvolat výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
> *výraz noexcept*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *konstantní výraz* **)**  
  
### <a name="parameters"></a>Parametry  
 *konstantní výraz*  
 Konstantní výraz typu `bool` který udává, zda sada potenciální typy výjimek je prázdný. Nepodmíněné verze je ekvivalentní `noexcept(true)`.  
  
## <a name="remarks"></a>Poznámky  
 A *noexcept výraz* je typ z *specifikace výjimek*, příponu k deklaraci funkce, která představuje sadu typů, které může odpovídat obslužnou rutinu výjimky pro všechny výjimka, která ukončí funkce. Podmíněný operátor unární `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds `true`a jeho nepodmíněné synonymum `noexcept`, Zadejte, že sada potenciální typy výjimek, které můžete ukončit funkce je prázdný. To znamená funkce vyvolá výjimku, nikdy a nikdy umožňuje výjimku rozšíří mimo její obor. Operátor `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds `false`, nebo neexistenci těchto specifikace výjimek (jiných než pro destruktor nebo navrácení funkce), znamená, že sada potenciální výjimky, které můžete ukončit funkce sadu všechny typy.  
 
 Označit funkce jako `noexcept` pouze v případě, že všechny funkce, které volá, buď přímo nebo nepřímo, jsou také `noexcept` nebo `const`. Kompilátor nekontroluje nutně každá cesta kódu pro výjimky, které může být až bublinový `noexcept` funkce. Pokud výjimku ukončete vnějším oboru funkce označena `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) je volána hned, a není zaručeno, že bude volána destruktory všechny objekty v oboru. Použití `noexcept` místo specifikátor dynamické výjimka `throw`, který je zastaralé v C ++ 11 a novější a není plně implementované v sadě Visual Studio. Doporučujeme vám použít `noexcept` všechny funkce, která umožňuje nikdy výjimku šířit zásobníkem volání. Pokud je deklarovaná funkci `noexcept`, umožňuje kompilátoru ke generování efektivnější kód v několika různých kontextů.    
  
## <a name="example"></a>Příklad  
Funkce šablony, který kopíruje její argument může být deklarován `noexcept` za předpokladu, že objekt kopírovány je prostý starý datový typ (POD). Tato funkce může deklarovat takto:  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek C++](../cpp/cpp-exception-handling.md) [specifikace výjimek (throw, noexcept)](../cpp/exception-specifications-throw-cpp.md)