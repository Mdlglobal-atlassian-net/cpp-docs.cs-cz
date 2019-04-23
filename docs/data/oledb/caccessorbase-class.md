---
title: CAccessorBase – třída
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 34c92f9057f2273d57b69bdb42c49a81923c3d2a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034949"
---
# <a name="caccessorbase-class"></a>CAccessorBase – třída

Všechny přistupující objekty v šablonách technologie OLE DB odvozovat z této třídy. `CAccessorBase` Umožňuje spravovat několik přístupových objektů jedné sady řádků. Také poskytuje vazby pro parametry a výstupní sloupce.

## <a name="syntax"></a>Syntaxe

```cpp
// Replace with syntax
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Zavřít](#close)|Zavře přístupové objekty.|
|[GetHAccessor](#geth)|Načte popisovač přistupujícího objektu.|
|[GetNumAccessors](#getnum)|Získá počet přistupující objekty vytvořené třídy.|
|[IsAutoAccessor](#isauto)|Ověřuje, zda je zadaný přistupující objekt automaticky přistupující objekt.|
|[ReleaseAccessors](#release)|Uvolní přístupové objekty.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="close"></a> CAccessorBase::Close

Zavře přístupové objekty.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Je nutné volat [releaseaccessors –](../../data/oledb/caccessorbase-releaseaccessors.md) první.

## <a name="geth"></a> CAccessorBase::GetHAccessor

Načte popisovač přistupujícího objektu zadaného přístupového objektu.

### <a name="syntax"></a>Syntaxe

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
[in] Číslo nula posun pro přistupující objekt.

### <a name="return-value"></a>Návratová hodnota

Popisovač přistupujícího objektu.

## <a name="getnum"></a> CAccessorBase::GetNumAccessors

Získá počet přistupující objekty vytvořené třídy.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet přistupující objekty vytvořené třídy.

## <a name="isauto"></a> CAccessorBase::IsAutoAccessor

Vrátí true, pokud je během operace přesunu automaticky načíst data pro přistupující objekt.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
[in] Číslo nula posun pro přistupující objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** Pokud je přistupující objekt automaticky přistupující objekt. V opačném případě vrátí **false**.

## <a name="release"></a> CAccessorBase::ReleaseAccessors

Uvolní přistupující objekty vytvořené třídy.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` rozhraní pro objekt modelu COM, pro kterou byly vytvořeny přístupové objekty.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Volá se z [CAccessorRowset::Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase – třída](../../data/oledb/caccessorbase-class.md)