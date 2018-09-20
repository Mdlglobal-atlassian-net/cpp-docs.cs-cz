---
title: Cgopherlocator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d9309917fe89abbf3679060898861e1c698d660
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445838"
---
# <a name="cgopherlocator-class"></a>Cgopherlocator – třída

Získá gopher "Lokátor" ze serveru gopher, určí typ lokátoru a zpřístupní Lokátor [cgopherfilefind –](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členy jsou zastaralé, protože nebude fungovat na platformě Windows XP, ale budou i nadále fungovat na starší platformy.

## <a name="syntax"></a>Syntaxe

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Vytvoří `CGopherLocator` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyzuje gopher Lokátor a určuje jeho atributy.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Přímý přístup k znaků uložených v `CGopherLocator` objektu jako řetězec stylu C.|

## <a name="remarks"></a>Poznámky

Aplikace musí získat Lokátor gopher serveru předtím, než bylo možné získat informace z tohoto serveru. Jakmile obsahuje Lokátor, je nutné považovat za Lokátor neprůhledné token.

Každý gopher vyvolal atributy, které určují typ souboru nebo na serveru nalezen. Zobrazit [GetLocatorType](#getlocatortype) seznam typy lokátorů gopher.

Aplikace obvykle používá pro volání Lokátor [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) načíst konkrétní informace.

Další informace o tom, `CGopherLocator` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator

Tato členská funkce je volána k vytvoření `CGopherLocator` objektu.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
Odkaz na konstantu `CGopherLocator` objektu.

### <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CGopherLocator` objektu přímo. Namísto toho zavolejte metodu [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) k vytvoření a vrátí ukazatel `CGopherLocator` objektu.

##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType

Voláním této členské funkce, chcete-li získat typ lokátoru.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parametry

*dwRef*<br/>
Odkaz na DWORD, který se zobrazí typ lokátoru. Zobrazit **poznámky** tabulka obsahující typy Lokátor.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

Možné typy jsou následující:

|Hodnota|Význam|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Textový soubor ASCII.|
|GOPHER_TYPE_DIRECTORY|Adresář další položky Gopher.|
|GOPHER_TYPE_CSO|Server CSO telefonního seznamu.|
|GOPHER_TYPE_ERROR|Určuje chybovou podmínku.|
|GOPHER_TYPE_MAC_BINHEX|Macintosh soubor ve formátu BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Soubor archivu DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Soubor kódování uuencode.|
|GOPHER_TYPE_INDEX_SERVER|Server indexu.|
|GOPHER_TYPE_TELNET|Telnet Server.|
|GOPHER_TYPE_BINARY|Binární soubor.|
|GOPHER_TYPE_REDUNDANT|Duplicitní serveru. Informace obsažené v rámci je duplicitní primárního serveru. Poslední položky adresáře, které nemají typ GOPHER_TYPE_REDUNDANT je primární server.|
|GOPHER_TYPE_TN3270|TN3270 serveru.|
|GOPHER_TYPE_GIF|Soubor grafiky ve formátu GIF.|
|GOPHER_TYPE_IMAGE|Soubor obrázku.|
|GOPHER_TYPE_BITMAP|Soubor rastrového obrázku.|
|GOPHER_TYPE_MOVIE|Video souboru.|
|GOPHER_TYPE_SOUND|Zvukový soubor.|
|GOPHER_TYPE_HTML|Dokument HTML.|
|GOPHER_TYPE_PDF|Soubor PDF.|
|GOPHER_TYPE_CALENDAR|Soubor kalendáře.|
|GOPHER_TYPE_INLINE|Vložený soubor.|
|GOPHER_TYPE_UNKNOWN|Typ položky neznámý.|
|GOPHER_TYPE_ASK|Požádejte + položky.|
|GOPHER_TYPE_GOPHER_PLUS|Gopher + položky.|

##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR

Tento operátor užitečná přetypování poskytuje způsob pro přístup k C řetězec zakončený hodnotou null obsažené v `CGopherLocator` objektu.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku řetězec data.

### <a name="remarks"></a>Poznámky

Žádné znaky jsou zkopírovány; je vrácen pouze ukazatel.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)
