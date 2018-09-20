---
title: Interfacetraits::cancastto – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 705b495e3f6d626a742fd1a63989c8cc658446a4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379658"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Název ukazatele na typ.

*riid*<br/>
ID rozhraní `Base`.

*ppv*<br/>
Pokud je tato operace úspěšná, *ppv* odkazuje na rozhraní určené typem `Base`. V opačném případě *ppv* je nastavena na **nullptr**.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je tato operace úspěšná a *ptr* přetypovat na ukazatel na `Base`; v opačném případě **false** .

## <a name="remarks"></a>Poznámky

Určuje, zda je zadaný ukazatel může být převeden na ukazatel na `Base`.

Další informace o `Base`, najdete v článku **veřejné definice TypeDef** tématu [interfacetraits – struktura](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[InterfaceTraits – struktura](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)