---
title: "_com_ptr_t – extraktory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c006c18b9e00e5c79ff686dfb31fa9ccf56fd4e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrt-extractors"></a>_com_ptr_t – extraktory
**Konkrétní Microsoft**  
  
 Extrahuje zapouzdřený ukazatel rozhraní COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## <a name="remarks"></a>Poznámky  
  
-   **operátor Interface\***  vrátí ukazatel zapouzdřené rozhraní, které mohou být **NULL**.  
  
-   **operátor Interface &** vrátí odkaz na ukazatel zapouzdřené rozhraní a vyvolá chybu, pokud je ukazatel **NULL**.  
  
-   **operátor\***  umožňuje inteligentní ukazatele objektu tak, aby fungoval jako by šlo rozhraní skutečný obsah zapouzdřeného při Zrušením odkazu.  
  
-   **Operator ->** umožňuje inteligentní ukazatele objektu tak, aby fungoval jako by šlo rozhraní skutečný obsah zapouzdřeného při Zrušením odkazu.  
  
-   **operátor &** uvolní všechny ukazatel zapouzdřené rozhraní jeho nahrazením **NULL**a vrátí adresu zapouzdřené ukazatele. To umožňuje inteligentní ukazatele mají být předány podle adresy funkci, která má **out** parametr, pomocí kterého se vrátí ukazatele rozhraní.  
  
-   **operátor bool** umožňuje objekt chytré ukazatele pro použití v podmíněným výrazem. Tento operátor vrací **true** Pokud je ukazatel není **NULL**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)