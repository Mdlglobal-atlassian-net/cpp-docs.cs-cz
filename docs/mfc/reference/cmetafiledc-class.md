---
title: CMetaFileDC – třída
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369953"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC – třída

Implementuje metasoubor systému Windows, který obsahuje posloupnost příkazů rozhraní grafického zařízení (GDI), které můžete přehrát a vytvořit požadovaný obrázek nebo text.

## <a name="syntax"></a>Syntaxe

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Vytvoří `CMetaFileDC` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMetaFileDC::Zavřít](#close)|Zavře kontext zařízení a vytvoří popisovač metasouboru.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Zavře kontext zařízení rozšířené metasouboru a vytvoří popisovač rozšířené metasouboru.|
|[CMetaFileDC::Vytvořit](#create)|Vytvoří kontext zařízení metasouboru systému `CMetaFileDC` Windows a připojí jej k objektu.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Vytvoří kontext zařízení metasouboru pro metasoubor rozšířeného formátu.|

## <a name="remarks"></a>Poznámky

Chcete-li implementovat metasoubor `CMetaFileDC` systému Windows, nejprve vytvořte objekt. Vyvolat `CMetaFileDC` konstruktor, pak volat [Vytvořit](#create) členovou funkci, která vytvoří kontext zařízení `CMetaFileDC` metasouboru systému Windows a připojí jej k objektu.

Dále odešlete `CMetaFileDC` objektu posloupnost příkazů CDC GDI, které chcete přehrát. Lze použít pouze ty příkazy GDI, které vytvářejí výstup, například `MoveTo` a `LineTo`, .

Po odeslání požadovaných příkazů do metasouboru `Close` volejte členskou funkci, která zavře kontexty zařízení metasouboru a vrátí popisovač metasouboru. Potom zlikvidujte `CMetaFileDC` objekt.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) pak můžete použít popisovač metasouboru k opakovanému přehrání metasouboru. Metasoubor může být také manipulován o funkcích systému Windows, jako je [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), který zkopíruje metasoubor na disk.

Pokud metasoubor již není potřeba, odstraňte jej z paměti pomocí funkce [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows.

Můžete také implementovat `CMetaFileDC` objekt tak, aby mohl zpracovávat výstupní volání `GetTextExtent`a atribut GDI volání, jako je například . Takový metasoubor je flexibilnější a může snadněji znovu použít obecný kód GDI, který se často skládá ze kombinace volání výstupu a atributu. Třída `CMetaFileDC` zdědí dva kontexty zařízení `m_hDC` a `m_hAttribDC`, z CDC. Kontext `m_hDC` zařízení zpracovává všechna výstupní volání [CDC](../../mfc/reference/cdc-class.md) `m_hAttribDC` GDI a kontext zařízení zpracovává všechna volání atributu CDC GDI. Za normálních okolností tyto dva kontexty zařízení odkazují na stejné zařízení. V případě `CMetaFileDC`, je atribut DC ve výchozím nastavení nastaven na hodnotu NULL.

Vytvořte druhý kontext zařízení, který odkazuje na obrazovku, tiskárnu nebo zařízení `SetAttribDC` jiné než metasoubor, `m_hAttribDC`pak volání členské funkce přidružit nový kontext zařízení s . GDI výzvy k informacím budou `m_hAttribDC`nyní přesměrovány na nové . Výstupní volání GDI `m_hDC`přejde na , který představuje metasoubor.

Další informace `CMetaFileDC`naleznete v tématu [Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC::Zavřít

Zavře kontext zařízení metasouboru a vytvoří popisovač metasouboru systému Windows, který lze použít k přehrání metasouboru pomocí členské funkce [CDC::PlayMetaFile.](../../mfc/reference/cdc-class.md#playmetafile)

```
HMETAFILE Close();
```

### <a name="return-value"></a>Návratová hodnota

Platný HMETAFILE, pokud je funkce úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Popisovač metasouborů systému Windows lze také použít k manipulaci s metasouborem s funkcemi systému Windows, jako je [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Po použití odstraňte metasoubor voláním funkce [Windows DeleteMetaFile.](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced

Zavře kontext zařízení rozšířené metasouboru a vrátí popisovač, který identifikuje metasoubor rozšířeného formátu.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač rozšířené metasouboru, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Aplikace může použít popisovač rozšířené metasouboru vrácené touto funkcí k provedení následujících úloh:

- Zobrazení obrázku uloženého v rozšířeném metasouboru

- Vytvoření kopií rozšířeného metasouboru

- Výčet, úprava nebo kopírování jednotlivých záznamů v rozšířeném metasouboru

- Načtení volitelného popisu obsahu metasouboru ze záhlaví rozšířeného metasouboru

- Načtení kopie rozšířeného metasouboru záhlaví

- Načtení binární kopie rozšířeného metasouboru

- Výčet barev v volitelné paletě

- Převod metasouboru rozšířeného formátu na metasoubor ve formátu Windows

Když aplikace již nepotřebuje rozšířené metasouboru popisovač, by měla uvolnit `DeleteEnhMetaFile` popisovač voláním win32 funkce.

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC

Vytvořte `CMetaFileDC` objekt ve dvou krocích.

```
CMetaFileDC();
```

### <a name="remarks"></a>Poznámky

Nejprve `CMetaFileDC`volejte , `Create`a pak volejte , který vytvoří kontext `CMetaFileDC` zařízení metasouboru systému Windows a připojí jej k objektu.

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC::Vytvořit

Vytvořte `CMetaFileDC` objekt ve dvou krocích.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parametry

*lpszNázev_souboru*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null. Určuje název souboru metasouboru, který má být vytvořit. Pokud *je název souboru LPSZ* NULL, vytvoří se nový metasoubor v paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nejprve zavolejte `CMetaFileDC`konstruktoru `Create`, pak volání , který vytvoří kontext `CMetaFileDC` zařízení metasouboru systému Windows a připojí jej k objektu.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC::CreateEnhanced

Vytvoří kontext zařízení pro metasoubor rozšířeného formátu.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parametry

*příkaz pDCRef*<br/>
Identifikuje referenční zařízení pro rozšířený metasoubor.

*název souboru lpsz*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null. Určuje název souboru rozšířeného metasouboru, který má být vytvořen. Pokud je tento parametr NULL, rozšířený metasoubor je založen na paměti a jeho obsah `DeleteEnhMetaFile` se ztratí, když je objekt zničen nebo když je volána funkce Win32.

*lpBounds*<br/>
Odkazuje na datovou strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) který určuje rozměry v jednotkách HIMETRIC (v krocích po 0,01 milimetru) obrázku, který má být uložen v rozšířeném metasouboru.

*lpszDescription*<br/>
Odkazuje na řetězec s nulovým ukončením, který určuje název aplikace, která vytvořila obrázek, a také název obrázku.

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení pro rozšířený metasoubor, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Tento řadič domény lze použít k uložení obrázku nezávislého na zařízení.

Systém Windows používá referenční zařízení identifikované parametrem *pDCRef* k zaznamenání rozlišení a jednotek zařízení, na kterém se původně objevil obrázek. Pokud je parametr *pDCRef* NULL, použije aktuální zobrazovací zařízení jako referenci.

Levé a horní členy `RECT` datové struktury, na které poukazuje parametr *lpBounds,* musí být menší než pravý a dolní člen. Body podél okrajů obdélníku jsou zahrnuty na obrázku. Pokud *lpBounds* je NULL, rozhraní grafického zařízení (GDI) vypočítá rozměry nejmenší obdélník, který můžete uzavřít obrázek nakreslený aplikací. Parametr *lpBounds* by měl být zadán tam, kde je to možné.

Řetězec odkazovaný parametrem *lpszDescription* musí obsahovat nulový znak mezi názvem aplikace a názvem obrázku a musí být ukončen dvěma prázdnými znaky – například "XYZ Graphics Editor\0Bald Eagle\0\0", kde \0 představuje prázdný znak. Pokud *lpszDescription* je NULL, neexistuje žádná odpovídající položka v záhlaví rozšířené metasouboru.

Aplikace používají řadič domény vytvořený touto funkcí k uložení grafického obrázku do rozšířeného metasouboru. Popisovač identifikující tento řadič domény může být předán libovolné funkci GDI.

Poté, co aplikace uloží obrázek do rozšířeného metasouboru, může obrázek zobrazit na libovolném výstupním zařízení voláním `CDC::PlayMetaFile` funkce. Při zobrazení obrázku používá systém Windows obdélník, na který odkazuje parametr *lpBounds* a data rozlišení z referenčního zařízení, k umístění a zmenšení velikosti obrázku. Kontext zařízení vrácený touto funkcí obsahuje stejné výchozí atributy přidružené k jakékoli nové dc.

Aplikace musí používat funkci `GetWinMetaFileBits` Win32 k převodu rozšířeného metasouboru do staršího formátu metasouboru systému Windows.

Název souboru rozšířeného metasouboru by měl používat . rozšíření EMF.

## <a name="see-also"></a>Viz také

[Třída CDC](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
