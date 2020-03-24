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
ms.openlocfilehash: e3b76be2a1f1edfcdc1139a3dd396835923c2b4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210688"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl – třída

Poskytuje implementaci rozhraní [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IConvertTypeImpl`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="interface-methods"></a>Metody rozhraní

|||
|-|-|
|[CanConvert](#canconvert)|Poskytuje informace o dostupnosti převodů typů pro příkaz nebo sadu řádků.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je povinné pro příkazy, sady řádků a sady řádků indexu. `IConvertTypeImpl` implementuje rozhraní delegováním do objektu převodu dodaného OLE DB.

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a>IConvertTypeImpl –:: CanConvert

Poskytuje informace o dostupnosti převodů typů pro příkaz nebo sadu řádků.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parametry

Viz [IConvertType:: CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Používá převod dat OLE DB v `MSADC.DLL`.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
