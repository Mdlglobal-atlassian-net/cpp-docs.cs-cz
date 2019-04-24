---
title: CDWordArray Class
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: 8cc67e62d905710ba5d63bf93c7b8aa1bf50f69c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206121"
---
# <a name="cdwordarray-class"></a>CDWordArray Class

Podporuje pole s 32bitovými dvojitými slovy.

## <a name="syntax"></a>Syntaxe

```
class CDWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CDWordArray` jsou podobné jako u členských funkcí třídy [cobarray –](../../mfc/reference/cobarray-class.md). Z důvodu podobnosti, můžete použít `CObArray` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení `CObject` ukazatele jako parametr funkce nebo návratová hodnota, nahraďte `DWORD`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole. v případě potřeby se zvětší pole.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli; v případě potřeby se zvětší pole.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje jiného objektu array do pole. v případě potřeby se zvětší pole.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí odkaz na dočasný bajtů v rámci pole.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní všechny nevyužité paměti nad aktuální horní mez.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu na daném indexu.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet elementů v tomto poli.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet elementů v tomto poli.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere element na konkrétní indexu.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby se zvětší pole.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsažena v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObArray::operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CDWordArray` zahrnuje `IMPLEMENT_SERIAL` – makro na podporu serializace a výpis z jeho prvků. Pokud je pole x doubleword uložen do archivu, buď pomocí přetížených vložení ( **<<**) – operátor nebo se `Serialize` členská funkce, každý element je, v důsledku, serializovat.

> [!NOTE]
>  Před použitím pole, použijte `SetSize` vytvoření jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidání prvků pole způsobí, že ho bude často nevyčerpané a zkopírovat. Časté realokace a kopírování jsou neefektivní a může fragmentovat paměti.

Pokud potřebujete ladit výstup z jednotlivých prvků v poli, je nutné nastavit hloubka `CDumpContext` objektu na hodnotu 1 nebo větší.

Další informace o používání `CDWordArray`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CObArray – třída](../../mfc/reference/cobarray-class.md)
