---
title: DontUseNewUseMake::operator new – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99e82de06f64816521c47c78648108a9ae815279
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443225"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator new – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parametry

*__unnamed0*<br/>
Nepojmenovaný parametr, který určuje počet bajtů paměti k přidělení.

*umístění*<br/>
Typ, který má být přiděleny.

## <a name="return-value"></a>Návratová hodnota

Poskytuje způsob, jak předat další argumenty, pokud přetížíte operátor **nové**.

## <a name="remarks"></a>Poznámky

Přetížení operátoru **nové** a brání použití v `RuntimeClass`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[DontUseNewUseMake – třída](../windows/dontusenewusemake-class.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)