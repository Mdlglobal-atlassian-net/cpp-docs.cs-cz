---
title: CSettingsStoreSP – třída
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318455"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP – třída

Třída `CSettingsStoreSP` je pomocná třída, kterou můžete použít k vytvoření instancí [třídy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="syntax"></a>Syntaxe

```
class CSettingsStoreSP
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Vytvoří `CSettingsStoreSP` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSettingsStoreSP::Vytvořit](#create)|Vytvoří instanci třídy, která `CSettingsStore`je odvozena z aplikace .|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Nastaví třídu runtime. Metoda `Create` používá runtime třídy k určení, jakou třídu objektů vytvořit.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|`m_dwUserData`|Vlastní uživatelská data uložená v objektu. `CSettingsStoreSP` Tato data zadáte v konstruktoru objektu. `CSettingsStoreSP`|
|`m_pRegistry`|-derived `CSettingsStore`objekt, `Create` který metoda vytvoří.|

## <a name="remarks"></a>Poznámky

Třídu `CSettingsStoreSP` můžete použít k přesměrování všech operací registru knihovny MFC do jiných umístění, například do souboru XML nebo do databáze. Postupujte přitom takto:

1. Vytvořte třídu `CMyStore`(například) `CSettingsStore`a odvodit ji z .

1. Pomocí [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) a [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) makra s vlastní `CSettingsStore` třídou povolte dynamické vytváření.

1. Přepsat virtuální funkce a `Read` implementovat a `Write` funkce ve vlastní třídě. Implementujte všechny další funkce pro čtení a zápis dat do požadovaného umístění.

1. Ve vaší aplikaci volání `CSettingsStoreSP::SetRuntimeClass` a předání v ukazatel na [CRuntimeClass struktury](../../mfc/reference/cruntimeclass-structure.md) získané z vaší třídy.

Vždy, když rozhraní obvykle přístup k registru, bude nyní dynamicky konstanci vlastní třídy a použít ji ke čtení nebo zápisu dat.

`CSettingsStoreSP::SetRuntimeClass`používá globální statickou proměnnou. Proto je k dispozici pouze jeden vlastní úložiště současně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP::Vytvořit

Vytvoří novou instanci objektu, který je odvozen z [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bAdmin*<br/>
[v] Logický parametr, který určuje, `CSettingsStore` zda je objekt vytvořen v režimu správce.

*bReadOnly*<br/>
[v] Logický parametr, který určuje, `CSettingsStore` zda je objekt vytvořen pro přístup jen pro čtení.

### <a name="return-value"></a>Návratová hodnota

Odkaz na nově `CSettingsStore` vytvořený objekt.

### <a name="remarks"></a>Poznámky

Můžete použít metodu [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) k určení, jaký typ objektu `CSettingsStoreSP::Create` vytvoří. Ve výchozím nastavení tato `CSettingsStore` metoda vytvoří objekt.

Pokud vytvoříte `CSettingsStore` objekt v režimu správce, bude HKEY_LOCAL_MACHINE výchozí umístění pro veškerý přístup k registru. V opačném případě je HKEY_CURRENT_USER výchozí umístění pro veškerý přístup k registru.

Pokud *je bAdmin* TRUE, aplikace musí mít práva pro správu. V opačném případě se nezdaří při pokusu o přístup k registru.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `Create` používat metodu třídy. `CSettingsStoreSP`

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP

Vytvoří objekt [třídy CSettingsStoreSP.](../../mfc/reference/csettingsstoresp-class.md)

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
[v] Uživatelem definovaná `CSettingsStoreSP` data, která objekt ukládá.

### <a name="remarks"></a>Poznámky

Objekt `CSettingsStoreSP` ukládá data z *dwUserData* v `m_dwUserData`proměnné chráněného člena .

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass

Nastaví třídu runtime. Metoda [CSettingsStoreSP::Create](#create) používá třídu runtime k určení typu objektu, který má být vytvořit.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Parametry

*pRTI*<br/>
[v] Ukazatel na informace o třídě runtime pro třídu odvozenou z [třídy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; FALSE, pokud třída identifikovaná *pRTI* `CSettingsStore`není odvozena z .

### <a name="remarks"></a>Poznámky

[Třídu CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) můžete použít k `CSettingsStore`odvození tříd z aplikace . Metodu `SetRuntimeClass` použijte, pokud chcete vytvořit objekty vlastní třídy, která je odvozena od `CSettingsStore`.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CSettingsStore](../../mfc/reference/csettingsstore-class.md)
