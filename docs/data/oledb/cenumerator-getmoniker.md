---
title: CEnumerator::GetMoniker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
dev_langs:
- C++
helpviewer_keywords:
- GetMoniker method
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5fe2f440d7aad0fd3aca92d6e7de308345dd8f32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097702"
---
# <a name="cenumeratorgetmoniker"></a>CEnumerator::GetMoniker
Analyzuje zobrazovaný název pro extrahování součást řetězec, který mohou být převedeny na přezdívka.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  


HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ppMoniker*  
 [out] Přezdívka analyzovat z zobrazovaný název ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) aktuálního řádku.  
  
 *lpszDisplayName*  
 [v] Zobrazovaný název analyzovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CEnumerator – třída](../../data/oledb/cenumerator-class.md)