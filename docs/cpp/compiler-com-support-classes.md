---
title: Třídy podpory kompilátoru modelu COM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc931e643235bc6edb4a1121628ac5185b76cc7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402546"
---
# <a name="compiler-com-support-classes"></a>Třídy podpory kompilátoru modelu COM
**Specifické pro Microsoft**  
  
 Standardní třídy se používá pro podporu některých typů modelu COM. Třídy jsou definovány v \<comdef.h > a souborech hlaviček generovaných z knihovny typů.  
  
|Třída|Účel|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|Zabalí `BSTR` typ poskytnout užitečné operátory a metody.|  
|[_com_error](../cpp/com-error-class.md)|Definuje objekt chyby vyvolané [_com_raise_error](../cpp/com-raise-error.md) ve většině chyb.|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|Zapouzdřuje ukazatele rozhraní modelu COM a automatizuje vyžaduje volání `AddRef`, `Release`, a `QueryInterface`.|  
|[_variant_t](../cpp/variant-t-class.md)|Zabalí `VARIANT` typ poskytnout užitečné operátory a metody.|  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Podpora kompilátoru modelu COM](../cpp/compiler-com-support.md)   
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)   
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)