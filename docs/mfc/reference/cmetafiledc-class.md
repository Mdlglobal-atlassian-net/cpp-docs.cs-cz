---
title: CMetaFileDC – – třída
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
ms.openlocfilehash: 61e8442c085a5be0a7266409daf973bf63f52a7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505508"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC – – třída

Implementuje metasoubor systému Windows, který obsahuje posloupnost příkazů GDI (Graphics Device Interface), které můžete přehrát a vytvořit požadovaný obrázek nebo text.

## <a name="syntax"></a>Syntaxe

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|`CMetaFileDC` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|Zavře kontext zařízení a vytvoří popisovač metasouboru.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Zavře kontext zařízení s rozšířeným metasouborem a vytvoří popisovač Enhanced Metafile.|
|[CMetaFileDC::Create](#create)|Vytvoří kontext zařízení Windows Metafile a připojí ho k `CMetaFileDC` objektu.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Vytvoří kontext zařízení metasouboru pro formát metasouboru Enhanced-Format.|

## <a name="remarks"></a>Poznámky

Chcete-li implementovat metasoubor systému Windows, nejprve `CMetaFileDC` vytvořte objekt. Vyvolejte `CMetaFileDC` konstruktor a pak zavolejte funkci vytvořit členskou funkci, která vytvoří kontext zařízení Windows Metafile a připojí ho k objektu. [](#create) `CMetaFileDC`

V dalším kroku `CMetaFileDC` odešlete objekt sekvenci příkazů nástroje CDC pro rozhraní GDI, které máte v úmyslu přehrát znovu. Pouze příkazy GDI, které vytvářejí výstup, například `MoveTo` a `LineTo`, lze použít.

Po odeslání požadovaných příkazů do metasouboru volejte `Close` členskou funkci, která zavře kontexty zařízení metasouboru a vrátí popisovač metasouboru. `CMetaFileDC` Pak objekt odstraňte.

[CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) pak může použít popisovač metasouboru opakovaně k přehrání metasouboru. Metasoubor může také manipulovat s funkcemi systému Windows, jako je například [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), které kopírují metasoubor na disk.

Pokud už metasoubor nepotřebujete, odstraňte ho z paměti pomocí funkce [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows.

Můžete také implementovat `CMetaFileDC` objekt tak, aby mohl zpracovávat volání výstupu i volání v atributu, jako je například `GetTextExtent`. Takový metasoubor je flexibilnější a může snadněji znovu použít obecný kód GDI, který se často skládá ze směsi volání výstupů a atributů. Třída dědí dva kontexty `m_hDC` zařízení a `m_hAttribDC`, z CDC. `CMetaFileDC` Kontext zařízení zpracovává všechna volání `m_hAttribDC` výstupu rozhraní CDC a kontext zařízení zpracovává všechna volání atributů CDC rozhraní GDI. [](../../mfc/reference/cdc-class.md) `m_hDC` Obvykle tyto dva kontexty zařízení odkazují na stejné zařízení. V případě `CMetaFileDC`je atribut řadič domény ve výchozím nastavení nastaven na hodnotu null.

Vytvořte druhý kontext zařízení, který odkazuje na obrazovku, tiskárnu nebo jiné zařízení, než je metasoubor, a pak zavolejte `SetAttribDC` členskou funkci pro přidružení nového `m_hAttribDC`kontextu zařízení k. Volání GDI pro informace se nyní budou směrovat na nové `m_hAttribDC`. Výstupní volání GDI budou jít na `m_hDC`, což představuje metasoubor.

Další informace o `CMetaFileDC`najdete v tématu [Kontexty zařízení](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="close"></a>CMetaFileDC –:: Close

Zavře kontext zařízení metasouboru a vytvoří popisovač metasouboru systému Windows, který lze použít k přehrání metasouboru pomocí členské funkce [CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) .

```
HMETAFILE Close();
```

### <a name="return-value"></a>Návratová hodnota

Platný HMETAFILE, pokud je funkce úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Popisovač metasouboru Windows se dá použít taky k manipulaci s metasouborem s funkcemi Windows, jako je [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Odstraňte metasoubor po použití voláním funkce Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) .

##  <a name="closeenhanced"></a>CMetaFileDC –:: CloseEnhanced

Ukončí kontext zařízení s rozšířeným metasouborem a vrátí popisovač, který identifikuje metasoubor Enhanced-Format.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač Enhanced Metafile, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Aplikace může použít popisovač Enhanced-Metafile vrácený touto funkcí k provedení následujících úloh:

- Zobrazit obrázek uložený v rozšířeném metasouboru

- Vytváření kopií Enhanced Metafile

- Zobrazení výčtu, úpravy nebo kopírování jednotlivých záznamů v rozšířeném metasouboru

- Načíst volitelný popis obsahu metasouboru z hlavičky Enhanced Metafile

- Načíst kopii hlavičky Enhanced Metafile

- Načtení binární kopie Enhanced Metafile

- Zobrazení výčtu barev v volitelné paletě

- Převedení Enhanced-Format Metafile na metasoubor formátu Windows

Pokud aplikace již nepotřebuje rozšířený metasoubor, měl by vydávat popisovač voláním funkce Win32 `DeleteEnhMetaFile` .

##  <a name="cmetafiledc"></a>CMetaFileDC –:: CMetaFileDC –

`CMetaFileDC` Vytvořte objekt ve dvou krocích.

```
CMetaFileDC();
```

### <a name="remarks"></a>Poznámky

Nejdřív zavolejte `CMetaFileDC`a zavolejte `Create`, které vytvoří kontext zařízení Windows Metafile a `CMetaFileDC` připojí ho k objektu.

##  <a name="create"></a>CMetaFileDC –:: Create

`CMetaFileDC` Vytvořte objekt ve dvou krocích.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFilename*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null. Určuje název souboru metasouboru, který se má vytvořit. Pokud má *lpszFileName* hodnotu null, vytvoří se nový metasoubor v paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Nejdřív zavolejte konstruktor `CMetaFileDC`a potom zavolejte `Create`, který vytvoří kontext zařízení Windows Metafile a `CMetaFileDC` připojí ho k objektu.

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

Vytvoří kontext zařízení pro metasoubor Enhanced-Format.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parametry

*pDCRef*<br/>
Identifikuje referenční zařízení pro rozšířený metasoubor.

*lpszFileName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null. Určuje název souboru pro rozšířený metasoubor, který se má vytvořit. Pokud má tento parametr hodnotu null, je rozšířený metasoubor založen na paměti a jeho obsah ztracen při zničení objektu nebo při volání funkce Win32 `DeleteEnhMetaFile` .

*lpBounds*<br/>
Odkazuje na strukturu dat [Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který určuje rozměry obrázku v HIMETRICch jednotkách (v přírůstcích .01 – milimetry), které mají být uloženy v Enhanced Metafile.

*lpszDescription*<br/>
Odkazuje na řetězec zakončený nulou, který určuje název aplikace, která vytvořila obrázek, a také nadpis obrázku.

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení pro rozšířený metasoubor, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Tento řadič domény se dá použít k uložení obrázku nezávislého na zařízení.

Systém Windows používá referenční zařízení identifikované parametrem *pDCRef* k zaznamenání rozlišení a jednotek zařízení, na které se obrázek původně objevil. Pokud má parametr *pDCRef* hodnotu null, použije se aktuální zobrazovací zařízení pro referenci.

Levý a horní člen struktury `RECT` dat, na který ukazuje parametr *lpBounds* , musí být menší než pravá a dolní počet členů v uvedeném pořadí. Body podél okrajů obdélníku jsou zahrnuty v obrázku. Pokud má *lpBounds* hodnotu null, rozhraní GDI (Graphics Device Interface) vypočítá rozměry nejmenšího obdélníku, který může uzavřít obrázek vykreslený aplikací. Je-li to možné, měl by být zadán parametr *lpBounds* .

Řetězec, na který ukazuje parametr *lpszDescription* , musí obsahovat znak null mezi názvem aplikace a názvem obrázku a musí končit dvěma znaky null, například "XYZ Graphics Editor\0Bald Eagle\0\0", kde \ 0 představuje znak null. Pokud má *lpszDescription* hodnotu null, neexistuje odpovídající záznam v hlavičce Enhanced-Metafile.

Aplikace používají řadič domény vytvořený touto funkcí k uložení grafického obrázku do rozšířeného metasouboru. Popisovač identifikující tento řadič domény je možné předat libovolné funkci GDI.

Když aplikace uloží obrázek do rozšířeného metasouboru, může zobrazit obrázek na jakémkoli výstupním zařízení voláním `CDC::PlayMetaFile` funkce. Při zobrazení obrázku používá systém Windows obdélník, na který odkazuje parametr *lpBounds* , a data o rozlišení z referenčního zařízení k umístění a škálování obrázku. Kontext zařízení vrácený touto funkcí obsahuje stejné výchozí atributy, které jsou přidružené k libovolnému novému řadiči domény.

Aplikace musí pomocí funkce Win32 `GetWinMetaFileBits` převést rozšířený metasoubor na starší formát Windows Metafile.

Název souboru pro rozšířený metasoubor by měl používat. Přípona EMF.

## <a name="see-also"></a>Viz také:

[CDC – třída](../../mfc/reference/cdc-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
