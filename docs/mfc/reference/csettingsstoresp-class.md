---
title: CSettingsStoreSP Class
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
ms.openlocfilehash: 5c7a992b983552340ebe21e59d2ee9a667841ec0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339523"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP Class

`CSettingsStoreSP` Třída je pomocná třída, která můžete použít k vytvoření instance [csettingsstore – třída](../../mfc/reference/csettingsstore-class.md).

## <a name="syntax"></a>Syntaxe

```
class CSettingsStoreSP
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Vytvoří `CSettingsStoreSP` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSettingsStoreSP::Create](#create)|Vytvoří instanci třídy, která je odvozena od `CSettingsStore`.|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Nastaví třídu modulu runtime. `Create` Metoda třídy modulu runtime používá k určení jaké třídu objektů, které chcete vytvořit.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|`m_dwUserData`|Vlastní uživatelská data, která je uložena v `CSettingsStoreSP` objektu. Zadat tato data v konstruktoru `CSettingsStoreSP` objektu.|
|`m_pRegistry`|`CSettingsStore`-Odvozené objekt, který `Create` metoda vytvoří.|

## <a name="remarks"></a>Poznámky

Můžete použít `CSettingsStoreSP` třídy přesměrovat všechny operace s registrem knihovny MFC do jiných umístění, jako je například soubor XML nebo databáze. Postupujte přitom takto:

1. Vytvořte třídu (například `CMyStore`) a jsou odvozeny z `CSettingsStore`.

1. Použití [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) a [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) makra s vlastní `CSettingsStore` třídy můžete povolit dynamické vytváření.

1. Přepsání virtuální funkce a provádět `Read` a `Write` funkce ve své vlastní třídě. Implementujte další funkce pro čtení a zápis dat do požadovaného umístění.

1. V aplikaci volat `CSettingsStoreSP::SetRuntimeClass` a předat ukazatel [CRuntimeClass – struktura](../../mfc/reference/cruntimeclass-structure.md) získané z vaší třídy.

Pokaždé, když se rozhraní by obvykle přistupovali k registru, bude nyní dynamicky vytvořit instanci vlastní třída a použít ke čtení nebo zápis dat.

`CSettingsStoreSP::SetRuntimeClass` používá globální statické proměnné. Jenom jeden vlastní úložiště je proto k dispozici v čase.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsettingsstore.h

##  <a name="create"></a>  CSettingsStoreSP::Create

Vytvoří novou instanci objektu, který je odvozen z [csettingsstore – třída](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bAdmin*<br/>
[in] Parametr logické hodnoty, která určuje, zda `CSettingsStore` objekt je vytvořen v režimu správce.

*bReadOnly*<br/>
[in] Parametr logické hodnoty, která určuje, zda `CSettingsStore` vytvoření objektu pro přístup jen pro čtení.

### <a name="return-value"></a>Návratová hodnota

Odkaz na nově vytvořený `CSettingsStore` objektu.

### <a name="remarks"></a>Poznámky

Můžete použít metodu [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) k určení, jaký typ objektu `CSettingsStoreSP::Create` vytvoří. Ve výchozím nastavení, tato metoda vytvoří `CSettingsStore` objektu.

Pokud jste vytvořili `CSettingsStore` objektu v režimu správce, je výchozím umístěním pro všechny přístup k registru HKEY_LOCAL_MACHINE. V opačném případě je výchozím umístěním pro všechny přístup k registru HKEY_CURRENT_USER.

Pokud *bAdmin* má hodnotu TRUE, aplikace musí mít administrativní oprávnění. V opačném případě dojde při pokusu o přístup k registru.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `Create` metodu `CSettingsStoreSP` třídy.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP

Vytvoří [csettingsstoresp – třída](../../mfc/reference/csettingsstoresp-class.md) objektu.

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
[in] Data definovaná uživatelem, který `CSettingsStoreSP` objektu úložiště.

### <a name="remarks"></a>Poznámky

`CSettingsStoreSP` Ukládají data z objektu *dwUserData* proměnné chráněný člen `m_dwUserData`.

##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass

Nastaví třídu modulu runtime. Metoda [CSettingsStoreSP::Create](#create) používá třídu runtime k určení typu objektu, který chcete vytvořit.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Parametry

*pRTI*<br/>
[in] Ukazatel na informace o třídě modulu runtime pro třídy odvozené z [csettingsstore – třída](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; FALSE, pokud třída identifikována *pRTI* není odvozen od `CSettingsStore`.

### <a name="remarks"></a>Poznámky

Můžete použít [csettingsstoresp – třída](../../mfc/reference/csettingsstoresp-class.md) odvozovat z `CSettingsStore`. Pomocí této metody `SetRuntimeClass` Pokud budete chtít vytvořit objekty tohoto vlastní třídu, která je odvozena od `CSettingsStore`.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore – třída](../../mfc/reference/csettingsstore-class.md)
