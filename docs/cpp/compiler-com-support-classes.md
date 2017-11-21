---
title: "Třídy podpory kompilátoru modelu COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_raise_error
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e2ec9f0814c976a5ea175e0cd62ab8e57b02f1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-com-support-classes"></a>Třídy podpory kompilátoru modelu COM
**Konkrétní Microsoft**  
  
 Standardní třídy se používají pro podporu některé typy COM. Třídy jsou definovány v comdef.h a soubory hlaviček vygenerovat z knihovny typů.  
  
|Třída|Účel|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|Zabalí `BSTR` typ zajistit užitečné operátory a metody.|  
|[_com_error](../cpp/com-error-class.md)|Definuje objekt chyba vyvolané [_com_raise_error –](../cpp/com-raise-error.md) ve většině chyb.|  
|[_com_ptr_t –](../cpp/com-ptr-t-class.md)|Zapouzdří ukazatele rozhraní COM a automatizuje vyžaduje volání `AddRef`, **verze**, a `QueryInterface`.|  
|[_variant_t](../cpp/variant-t-class.md)|Zabalí **VARIANT** typ zajistit užitečné operátory a metody.|  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Podpora kompilátoru modelu COM](../cpp/compiler-com-support.md)   
 [Globální funkce kompilátoru modelu COM](../cpp/compiler-com-global-functions.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)