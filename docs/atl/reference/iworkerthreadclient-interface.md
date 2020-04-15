---
title: Rozhraní IWorkerThreadClient
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 6a68f25f153a0ad2cf42ebfaa374ff63c5746fcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326300"
---
# <a name="iworkerthreadclient-interface"></a>Rozhraní IWorkerThreadClient

`IWorkerThreadClient`je rozhraní implementované klienty třídy [CWorkerThread.](../../atl/reference/cworkerthread-class.md)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface IWorkerThreadClient
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Zavřít handle](#closehandle)|Implementujte tuto metodu k uzavření popisovače přidruženého k tomuto objektu.|
|[Spuštění](#execute)|Implementujte tuto metodu ke spuštění kódu, když popisovač přidružený k tomuto objektu se stane signalizován.|

## <a name="remarks"></a>Poznámky

Implementujte toto rozhraní, pokud máte kód, který je třeba spustit v pracovním vlákně v reakci na popisovač, který se stane signalizován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implementujte tuto metodu k uzavření popisovače přidruženého k tomuto objektu.

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Rukojeť, která má být uzavřena.

### <a name="return-value"></a>Návratová hodnota

Vrátit S_OK na úspěch nebo chyba HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač předaný této metodě byl dříve přidružen k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou `IWorkerThreadClient::CloseHandle`implementaci .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Spustit

Implementujte tuto metodu ke spuštění kódu, když popisovač přidružený k tomuto objektu se stane signalizován.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Parametr uživatele.

*hObjekt*<br/>
Rukojeť, která se stala signalizována.

### <a name="return-value"></a>Návratová hodnota

Vrátit S_OK na úspěch nebo chyba HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač a DWORD/pointer předané této metodě byly dříve přidruženy k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou `IWorkerThreadClient::Execute`implementaci .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)<br/>
[Třída CWorkerThread](../../atl/reference/cworkerthread-class.md)
