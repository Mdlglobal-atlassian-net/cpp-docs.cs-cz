---
title: _com_ptr_t – extraktory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d63a09dec74fc1b7b41f8029dcff285b62b017f1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203224"
---
# <a name="comptrt-extractors"></a>_com_ptr_t – extraktory
**Specifické pro Microsoft**  
  
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
  
-   **operátor Interface** <strong>\*</strong> vrátí zapouzdřený ukazatel rozhraní, což může mít hodnotu NULL.  
  
-   **operátor Interface &** vrátí odkaz na zapouzdřený ukazatel rozhraní a vyvolá chybu, pokud ukazatel na hodnotu NULL.  
  
-   **operátor** <strong>\*</strong> umožní objektu inteligentního ukazatele tak, aby fungoval jako by šlo o skutečné zapouzdřené rozhraní při dereferenci.  
  
-   **Operator ->** umožní objektu inteligentního ukazatele tak, aby fungoval jako by šlo o skutečné zapouzdřené rozhraní při dereferenci.  
  
-   **operátor &** uvolní všechny zapouzdřený ukazatel rozhraní, nahraďte ho hodnotou NULL a vrátí adresu zapouzdřený ukazatel. To umožňuje inteligentní ukazatel adresou předat funkci, která má *si* parametr, jehož pomocí funkce vrátí ukazatel rozhraní.  
  
-   **Operator bool** umožní objektu inteligentního ukazatele se použije v podmíněných výrazech. Tento operátor vrátí hodnotu PRAVDA, pokud ukazatel není NULL.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)