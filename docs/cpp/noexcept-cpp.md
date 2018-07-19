---
title: noexcept (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 8eb8e6900dc12e4f176daf63bb711198f5e41429
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939286"
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** Určuje, zda může funkce vyvolat výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
> *noexcept: výraz*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept:**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *konstantní výraz* **)**  
  
### <a name="parameters"></a>Parametry  
 *constant-expression*  
 Konstantní výraz typu **bool** , která uvádí, zda se sada možných typů výjimek byla prázdná. Nepodmíněný verze je ekvivalentní `noexcept(true)`.  
  
## <a name="remarks"></a>Poznámky  
 A *noexcept výraz* je typ z *specifikace výjimky*, příponu k deklaraci funkce, která představuje sadu typů, které mohou odpovídat podvýrazu obslužné rutiny výjimky pro jakoukoliv výjimku, která ukončí funkce. Podmíněný operátor unární `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds **true**a jeho Nepodmíněný synonym `noexcept`, určuje, že sadu potenciální typy výjimek, které můžete ukončit funkci je prázdný. To znamená funkce vyvolá výjimku, nikdy a nikdy umožňuje výjimku mohly rozšířit mimo svůj rozsah. Operátor `noexcept(` *constant_expression* `)` kde *constant_expression* yeilds **false**, nebo neexistenci specifikaci výjimky (jiné než funkce destruktoru nebo zrušení přidělení), znamená, že sadu potenciální výjimky, které můžete ukončit funkci je sada všech typů.  
 
 Označit funkce jako `noexcept` pouze v případě, že všechny funkce, které volá, buď přímo nebo nepřímo, jsou také `noexcept` nebo **const**. Kompilátor nekontroluje nutně každá cesta kódu pro výjimky, které se může být až `noexcept` funkce. Pokud výjimku ukončit vnějším oboru funkce označené `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) okamžitě, je vyvolána a neexistuje žádná záruka, že budou vyvolány destruktory všech objektů v oboru. Použití `noexcept` namísto specifikátoru dynamických výjimek `throw()`, který je nyní zastaralý ve standardu. Doporučujeme vám použít `noexcept` pro všechny funkce, které nikdy umožňuje výjimce šíření výše zásobníkem volání. Když je funkce deklarovaná `noexcept`, umožňuje kompilátoru generovat efektivnější kód v několika různých kontextech. Další informace najdete v tématu [specifikace výjimek](exception-specifications-throw-cpp.md).   
  
## <a name="example"></a>Příklad  
Funkce šablony, který kopíruje svůj argument může být deklarován `noexcept` za předpokladu, že objekt kopírování je prostý původní typ dat (POD). Takové funkce může být deklarována takto:  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek jazyka C++](cpp-exception-handling.md) [specifikace výjimek (throw, noexcept)](exception-specifications-throw-cpp.md)