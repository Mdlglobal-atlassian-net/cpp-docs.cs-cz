---
title: _com_ptr_t::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7341695ad0cbc8384da859b80a72a63d8d52215f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Konkrétní Microsoft**  
  
 Zapouzdří ukazatel nezpracovaná rozhraní tento inteligentní ukazatel typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pInterface`  
 Nezpracovaný ukazatel rozhraní.  
  
 `fAddRef`  
 Pokud je **true**, pak `AddRef` je volána. Pokud je **false**, `_com_ptr_t` objekt trvá vlastnictví ukazatel nezpracovaná rozhraní bez volání `AddRef`.  
  
## <a name="remarks"></a>Poznámky  
  
-   **Připojit (**`pInterface`**)** `AddRef` není volán.     To je předán vlastnictví rozhraní `_com_ptr_t` objektu. **Verze** nazývá se sníží počet odkazů pro dříve zapouzdřené ukazatele.  
  
-   **Připojit (** `pInterface` **,**`fAddRef`**)** Pokud `fAddRef` je **true**, `AddRef` nazývá se zvýší odkaz počet pro ukazatel zapouzdřené rozhraní.       Pokud `fAddRef` je **false**tento `_com_ptr_t` objekt trvá vlastnictví ukazatel nezpracovaná rozhraní bez volání `AddRef`. **Verze** nazývá se sníží počet odkazů pro dříve zapouzdřené ukazatele.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)