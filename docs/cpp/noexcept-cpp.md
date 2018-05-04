---
title: noexcept (C++) | Microsoft Docs
ms.custom: ''
ms.date: 01/12/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noexcept_cpp
dev_langs:
- C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0cc12c5b82e1cb8cda8243020f91614fe840502
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** Určuje, zda funkce může vyvolat výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
> *výraz noexcept*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *konstantní výraz* **)**  
  
### <a name="parameters"></a>Parametry  
 *constant-expression*  
 Konstantní výraz typu `bool` který udává, zda sada potenciální typy výjimek je prázdný. Nepodmíněné verze je ekvivalentní `noexcept(true)`.  
  
## <a name="remarks"></a>Poznámky  
 A *noexcept výraz* je typ z *specifikace výjimek*, příponu k deklaraci funkce, která představuje sadu typů, které může odpovídat obslužnou rutinu výjimky pro všechny výjimka, která ukončí funkce. Podmíněný operátor unární `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds `true`a jeho nepodmíněné synonymum `noexcept`, Zadejte, že sada potenciální typy výjimek, které můžete ukončit funkce je prázdný. To znamená funkce vyvolá výjimku, nikdy a nikdy umožňuje výjimku rozšíří mimo její obor. Operátor `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds `false`, nebo neexistenci těchto specifikace výjimek (jiných než pro destruktor nebo navrácení funkce), znamená, že sada potenciální výjimky, které můžete ukončit funkce sadu všechny typy.  
 
 Označit funkce jako `noexcept` pouze v případě, že všechny funkce, které volá, buď přímo nebo nepřímo, jsou také `noexcept` nebo `const`. Kompilátor nekontroluje nutně každá cesta kódu pro výjimky, které může být až bublinový `noexcept` funkce. Pokud výjimku ukončete vnějším oboru funkce označena `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) je volána hned, a není zaručeno, že bude volána destruktory všechny objekty v oboru. Použití `noexcept` místo specifikátor dynamické výjimka `throw()`, který je ve standardní nyní zastaralá. Doporučujeme vám použít `noexcept` všechny funkce, která umožňuje nikdy výjimku šířit zásobníkem volání. Pokud je deklarovaná funkci `noexcept`, umožňuje kompilátoru ke generování efektivnější kód v několika různých kontextů. Další informace najdete v tématu [specifikace výjimek](exception-specifications-throw-cpp.md).   
  
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
 [Zpracování výjimek C++](cpp-exception-handling.md) [specifikace výjimek (throw, noexcept)](exception-specifications-throw-cpp.md)