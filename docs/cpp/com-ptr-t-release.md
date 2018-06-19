---
title: _com_ptr_t::Release | Microsoft Docs
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
ms.openlocfilehash: 9bf83b3f6ece4e8422f1ba8dbc5d1448da6bf0c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409641"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Konkrétní Microsoft**  
  
 Volání **verze** členské funkce **IUnknown** na ukazatel zapouzdřené rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void Release( );  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Volání `IUnknown::Release` na ukazatel zapouzdřené rozhraní, vyvolání `E_POINTER` chyby, pokud je tento ukazatel rozhraní **NULL**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_ptr_t – třída](../cpp/com-ptr-t-class.md)