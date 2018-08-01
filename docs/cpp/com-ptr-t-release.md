---
title: _com_ptr_t::Release | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5da56c3c85c17bcd2cd91f9fa5a5f8399e9528
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404272"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Specifické pro Microsoft**  
  
 Volání **vydání** členskou funkci `IUnknown` na zapouzdřený ukazatel rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Release( );  
```  
  
## <a name="remarks"></a>Poznámky  
 Volání `IUnknown::Release` na zapouzdřený ukazatel rozhraní, vyvolání `E_POINTER` chyby, pokud tento ukazatel rozhraní má hodnotu NULL.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)