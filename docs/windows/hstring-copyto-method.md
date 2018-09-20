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
ms.openlocfilehash: f8ea15c56bb974cc297c8fc396205d5f172e9bfd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388079"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo – metoda

Zkopíruje aktuální **HString** objektu na objekt HSTRING.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, který přijímá kopii.

## <a name="remarks"></a>Poznámky

Tato metoda volá [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)