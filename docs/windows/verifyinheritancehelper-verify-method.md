---
title: Verifyinheritancehelper::Verify – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfcbb57694fc18944d199c1d4c74d8c74a335783
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599112"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
static void Verify();
```

## <a name="remarks"></a>Poznámky

Testuje dvě rozhraní určeném aktuálním parametry šablony a určuje, zda jedno rozhraní je odvozena od druhé.

Chyba je vygenerován, pokud jedno rozhraní není odvozena od druhé.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[VerifyInheritanceHelper – struktura](../windows/verifyinheritancehelper-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)