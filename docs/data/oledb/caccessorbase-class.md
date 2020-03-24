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
ms.openlocfilehash: 8aef8a04d7adff903e21491a91014d55aab769da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212289"
---
# <a name="caccessorbase-class"></a>CAccessorBase – třída

Všechny přistupující objekty v šablonách OLE DB jsou odvozeny z této třídy. `CAccessorBase` umožňuje jedné sadě řádků spravovat více přístupových objektů. Poskytuje také vazbu pro oba parametry i výstupní sloupce.

## <a name="syntax"></a>Syntaxe

```cpp
// Replace with syntax
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Uzavírací](#close)|Zavře přistupující objekty.|
|[GetHAccessor](#geth)|Načte popisovač přistupujícího objektu.|
|[GetNumAccessors](#getnum)|Načte počet přístupových objektů vytvořených třídou.|
|[IsAutoAccessor](#isauto)|Testuje, zda je zadaný přístupový objekt autoaccess.|
|[ReleaseAccessors](#release)|Uvolňuje přistupující objekty.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="caccessorbaseclose"></a><a name="close"></a>CAccessorBase:: Close

Zavře přistupující objekty.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Nejdříve je nutné volat [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) .

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a>CAccessorBase:: GetHAccessor

Načte popisovač přistupujícího objektu zadaného přístupového objektu.

### <a name="syntax"></a>Syntaxe

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
pro Číslo nulového posunu pro přistupující objekt.

### <a name="return-value"></a>Návratová hodnota

Popisovač přistupujícího objektu.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a>CAccessorBase:: GetNumAccessors

Načte počet přístupových objektů vytvořených třídou.

### <a name="syntax"></a>Syntaxe

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet přístupových objektů vytvořených třídou.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a>CAccessorBase:: IsAutoAccessor

Vrátí hodnotu true, pokud jsou data automaticky načtena pro přistupující objekt během operace přesunutí.

### <a name="syntax"></a>Syntaxe

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametry

*nAccessor*<br/>
pro Číslo nulového posunu pro přistupující objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí **hodnotu true** , pokud je přistupující objekt autoaccess. V opačném případě vrátí **hodnotu false**.

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a>CAccessorBase:: ReleaseAccessors

Uvolňuje přistupující objekty vytvořené třídou.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na rozhraní `IUnknown` pro objekt COM, pro který byly vytvořeny přistupující objekty.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Volá se z [CAccessorRowset –:: Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase – třída](../../data/oledb/caccessorbase-class.md)
