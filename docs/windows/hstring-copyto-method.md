---
title: Hstring::CopyTo – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65d8e259b74bcdffbf11c6c96172d918f9db1b50
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570870"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo – metoda
Zkopíruje aktuální **HString** objektu na objekt HSTRING.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *str*  
 HSTRING, který přijímá kopii.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda volá [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)