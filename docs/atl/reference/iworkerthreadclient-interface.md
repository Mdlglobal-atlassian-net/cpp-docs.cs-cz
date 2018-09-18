---
title: Iworkerthreadclient – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c0261964f2e9c33f8a594a83e1b19c1db7be614
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069232"
---
# <a name="iworkerthreadclient-interface"></a>Iworkerthreadclient – rozhraní

`IWorkerThreadClient` představuje rozhraní implementované klienty [cworkerthread –](../../atl/reference/cworkerthread-class.md) třídy.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CloseHandle](#closehandle)|Implementujte tuto metodu za účelem zavřít popisovač asociovaném s tímto objektem.|
|[Execute](#execute)|Implementujte tuto metodu za účelem spouštění kódu, když se stane signalizován popisovač asociovaném s tímto objektem.|

## <a name="remarks"></a>Poznámky

Toto rozhraní implementují, když máte kód, který je potřeba provést v pracovní podproces v reakci na popisovač stávají signalizovanými.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implementujte tuto metodu za účelem zavřít popisovač asociovaném s tímto objektem.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Obslužná rutina bude uzavřen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač předaný této metodě byla dříve přidružená k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchý provádění `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implementujte tuto metodu za účelem spouštění kódu, když se stane signalizován popisovač asociovaném s tímto objektem.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Tento parametr.

*hObject*<br/>
Obslužná rutina, která má být signalizovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač a DWORD/ukazatel předaný této metodě byly dříve přidružená k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchý provádění `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread – třída](../../atl/reference/cworkerthread-class.md)
