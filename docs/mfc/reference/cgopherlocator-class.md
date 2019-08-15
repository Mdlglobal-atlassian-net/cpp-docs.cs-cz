---
title: CGopherLocator – třída
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: 9ce95a712af6502bff2a2502582a7fa843bf9653
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506161"
---
# <a name="cgopherlocator-class"></a>CGopherLocator – třída

Načte Lokátor typu gopher ze serveru gopher, určí typ lokátoru a zpřístupní Lokátor pro [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
>  Třídy `CGopherConnection` `CGopherFile` ,`CGopherLocator` , a jejich členové jsou zastaralí, protože nefungují na platformě Windows XP, ale budou fungovat i na `CGopherFileFind`starších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|`CGopherLocator` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyzuje Lokátor protokolu Gopher a určí jeho atributy.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CGopherLocator:: operator LPCTSTR](#operator_lpctstr)|Přímo přistupuje ke znakům uloženým `CGopherLocator` v objektu jako řetězec ve stylu jazyka C.|

## <a name="remarks"></a>Poznámky

Aby bylo možné získat informace z tohoto serveru, musí aplikace získat Lokátor serveru Gopher. Jakmile má lokátor, musí zacházet s lokátorem jako s neprůhledným tokenem.

Každý Lokátor protokolu Gopher má atributy, které určují typ nalezeného souboru nebo serveru. Seznam typů lokátorů protokolu Gopher najdete v tématu [GetLocatorType](#getlocatortype) .

Aplikace obvykle používá Lokátor pro volání [CGopherFileFind:: FindFile –](../../mfc/reference/cgopherfilefind-class.md#findfile) , aby bylo možné načíst konkrétní informaci.

Další informace o tom, `CGopherLocator` jak pracovat s jinými internetovými třídami knihovny MFC, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

Tato členská funkce je volána pro vytvoření `CGopherLocator` objektu.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
Odkaz na objekt konstanty `CGopherLocator` .

### <a name="remarks"></a>Poznámky

`CGopherLocator` Objekt nikdy nevytvoříte přímo. Místo toho zavolejte [CGopherConnection:: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) a vytvořte a vraťte ukazatel na `CGopherLocator` objekt.

##  <a name="getlocatortype"></a>CGopherLocator::GetLocatorType

Chcete-li získat typ lokátoru, zavolejte tuto členskou funkci.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parametry

*dwRef*<br/>
Odkaz na DWORD, který získá typ lokátoru. Tabulku typů lokátorů naleznete v tématu **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Možné typy jsou následující:

|Value|Význam|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Textový soubor ASCII.|
|GOPHER_TYPE_DIRECTORY|Adresář dalších položek protokolu Gopher.|
|GOPHER_TYPE_CSO|CSO server telefonního seznamu.|
|GOPHER_TYPE_ERROR|Označuje chybový stav.|
|GOPHER_TYPE_MAC_BINHEX|Soubor Macintosh ve formátu BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Archivní soubor systému DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|UUENCODE soubor.|
|GOPHER_TYPE_INDEX_SERVER|Server indexu.|
|GOPHER_TYPE_TELNET|Server Telnet.|
|GOPHER_TYPE_BINARY|Binární soubor.|
|GOPHER_TYPE_REDUNDANT|Duplicitní server. Informace obsažené v rámci jsou duplicitní s primárním serverem. Primárním serverem je poslední položka adresáře, která nemá typ GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|TN3270 Server.|
|GOPHER_TYPE_GIF|Soubor grafiky GIF.|
|GOPHER_TYPE_IMAGE|Soubor obrázku.|
|GOPHER_TYPE_BITMAP|Rastrový soubor.|
|GOPHER_TYPE_MOVIE|Filmový soubor.|
|GOPHER_TYPE_SOUND|Zvukový soubor.|
|GOPHER_TYPE_HTML|Dokument HTML.|
|GOPHER_TYPE_PDF|Soubor PDF.|
|GOPHER_TYPE_CALENDAR|Soubor kalendáře.|
|GOPHER_TYPE_INLINE|Vložený soubor.|
|GOPHER_TYPE_UNKNOWN|Typ položky je neznámý.|
|GOPHER_TYPE_ASK|Položka Ask +|
|GOPHER_TYPE_GOPHER_PLUS|Položka gopher +|

##  <a name="operator_lpctstr"></a>CGopherLocator:: operator LPCTSTR

Tento užitečný operátor přetypování poskytuje efektivní metodu pro přístup k řetězci jazyka C zakončeného hodnotou null obsaženým v `CGopherLocator` objektu.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Návratová hodnota

Znakový ukazatel na data řetězce.

### <a name="remarks"></a>Poznámky

Nejsou kopírovány žádné znaky; Vrátí se jenom ukazatel.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)
