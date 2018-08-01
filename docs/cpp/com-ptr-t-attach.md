---
title: _com_ptr_t::Attach | Dokumentace Microsoftu
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
ms.openlocfilehash: c48da9a0ff3b9cadf0b7e228f3108277154e8417
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402881"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Specifické pro Microsoft**  
  
 Zapouzdřuje nezpracovaný ukazatel rozhraní tohoto inteligentního ukazatele typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Attach( Interface* pInterface ) throw( );  
void Attach( Interface* pInterface, bool fAddRef ) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *pInterface*  
 Nezpracovaný ukazatel rozhraní.  
  
 *fAddRef*  
 Pokud je hodnota TRUE, pak `AddRef` je volána. Pokud má hodnotu FALSE, `_com_ptr_t` objekt převezme vlastnictví nezpracovaného ukazatele rozhraní bez volání `AddRef`.  
  
## <a name="remarks"></a>Poznámky  
  
-   **Připojení (***pInterface***)** `AddRef` není volána. To je předáno vlastnictví rozhraní `_com_ptr_t` objektu. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel.  
  
-   **Připojení (***pInterface* **,***fAddRef***)** Pokud *fAddRef* má hodnotu TRUE, `AddRef`nazývá se zvýší počet odkazů pro zapouzdřený ukazatel rozhraní.       Pokud *fAddRef* má hodnotu FALSE, to `_com_ptr_t` objekt převezme vlastnictví nezpracovaného ukazatele rozhraní bez volání `AddRef`. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)