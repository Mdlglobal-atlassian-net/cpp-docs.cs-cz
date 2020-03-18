---
title: CByteArray – třída
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 2453e7c040b9101f9c3a3b018e274b16e76ebea7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446347"
---
# <a name="cbytearray-class"></a>CByteArray – třída

Podporuje dynamická pole bajtů.

## <a name="syntax"></a>Syntaxe

```
class CByteArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CByteArray` jsou podobné členským funkcím třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CObArray` pro konkrétní členské funkce. Bez ohledu na to, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte bajt.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CByteArray::CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CByteArray:: Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CByteArray:: Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CByteArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CByteArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na bajt v rámci pole.|
|[CByteArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CByteArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CByteArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CByteArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CByteArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CByteArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CByteArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CByteArray::-Empty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CByteArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CByteArray:: funkce RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v konkrétním indexu.|
|[CByteArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CByteArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CByteArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CByteArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CByteArray` zahrnuje makro IMPLEMENT_SERIAL pro podporu serializace a dumpingu jeho prvků. Je-li pole bajtů uloženo do archivu, buď pomocí operátoru přetížení ( **<<** ), nebo pomocí členské funkce `Serialize`, každý prvek je následně serializován.

> [!NOTE]
>  Před použitím pole použijte `SetSize` k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Pokud potřebujete ladit výstup z jednotlivých prvků v poli, je nutné nastavit hloubku objektu `CDumpContext` na hodnotu 1 nebo vyšší.

Další informace o používání `CByteArray`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)
