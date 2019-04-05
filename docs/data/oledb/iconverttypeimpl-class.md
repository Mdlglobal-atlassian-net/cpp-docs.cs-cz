---
title: IConvertTypeImpl – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: 546a5a007f9e4c1c2a0e581eff2e7984947bdbb5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023721"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl – třída

Poskytuje implementaci [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IConvertTypeImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldb.h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[Canconvert –](#canconvert)|Poskytuje informace o dostupnosti převody typů příkazu nebo pro sadu řádků.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je povinná pro příkazy sady řádků a index sady řádků. `IConvertTypeImpl` implementuje rozhraní delegováním převodu objektu poskytnutých OLE DB.

## <a name="canconvert"></a> IConvertTypeImpl::CanConvert

Poskytuje informace o dostupnosti převody typů příkazu nebo pro sadu řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parametry

Zobrazit [IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) v *referenční informace pro OLE DB programátory*.

### <a name="remarks"></a>Poznámky

Používá převodu dat OLE DB v `MSADC.DLL`.

## <a name="see-also"></a>Viz také:

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)