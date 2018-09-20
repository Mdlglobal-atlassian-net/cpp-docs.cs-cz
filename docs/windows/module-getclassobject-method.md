---
title: Module::GetClassObject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a1b527d12e581c42fc9519e56d453f845e0b63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419714"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject – metoda

Načte mezipaměť objekty pro vytváření tříd.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
ID třídy.

*riid*<br/>
ID rozhraní, které požadujete.

*ppv*<br/>
Ukazatel na vráceného objektu.

*název_serveru*<br/>
Název serveru, který je zadán buď `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, nebo `ActivatableClass` – makro; nebo **nullptr** získat výchozí název serveru.

## <a name="return-value"></a>Návratová hodnota

## <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze pro model COM, nikoliv modul Windows Runtime. Tato metoda poskytuje pouze `IClassFactory` metody.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)