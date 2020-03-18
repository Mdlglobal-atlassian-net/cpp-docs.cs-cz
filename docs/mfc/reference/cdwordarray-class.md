---
title: CDWordArray – třída
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: f17caafd01bb5ddfa49afe378bfd79652149ebd8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447349"
---
# <a name="cdwordarray-class"></a>CDWordArray – třída

Podporuje pole 32 bitů doubleword.

## <a name="syntax"></a>Syntaxe

```
class CDWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CDWordArray` jsou podobné členským funkcím třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete použít referenční dokumentaci `CObArray` pro konkrétní členské funkce. Všude, kde vidíte `CObject` ukazatel jako parametr funkce nebo návratovou hodnotu, nahraďte `DWORD`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDWordArray::CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDWordArray:: Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CDWordArray:: Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CDWordArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CDWordArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na bajt v rámci pole.|
|[CDWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CDWordArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CDWordArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CDWordArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CDWordArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CDWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CDWordArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CDWordArray::-Empty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CDWordArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CDWordArray:: funkce RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v konkrétním indexu.|
|[CDWordArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CDWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CDWordArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CDWordArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CDWordArray` zahrnuje makro `IMPLEMENT_SERIAL` pro podporu serializace a dumpingu jeho prvků. Pokud je pole doubleword uloženo do archivu, buď pomocí operátoru přetíženého vkládání ( **<<** ), nebo pomocí členské funkce `Serialize`, každý prvek je naopak v tomto případě serializován.

> [!NOTE]
>  Před použitím pole použijte `SetSize` k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přiděleno a zkopírováno. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Pokud potřebujete ladit výstup z jednotlivých prvků v poli, je nutné nastavit hloubku objektu `CDumpContext` na hodnotu 1 nebo vyšší.

Další informace o používání `CDWordArray`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)
