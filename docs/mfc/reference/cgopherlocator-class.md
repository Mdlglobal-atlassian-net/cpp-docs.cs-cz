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
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373664"
---
# <a name="cgopherlocator-class"></a>CGopherLocator – třída

Získá gopher "lokátor" z gopher server, určuje typ lokátoru a zpřístupní lokátor [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
> Třídy `CGopherConnection` `CGopherFile`, `CGopherFileFind` `CGopherLocator` , a jejich členové byly zastaralé, protože nefungují na platformě systému Windows XP, ale budou pokračovat v práci na dřívějších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Vytvoří `CGopherLocator` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyzuje lokátor gopher a určuje jeho atributy.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherLocator::operátor LPCTSTR](#operator_lpctstr)|Přímo přistupuje `CGopherLocator` k znakům uloženým v objektu jako řetězec ve stylu C.|

## <a name="remarks"></a>Poznámky

Aplikace musí získat gopher server lokátor před tím, než může načíst informace z tohoto serveru. Jakmile má lokátor, musí považovat lokátor jako neprůhledný token.

Každý lokátor gopher má atributy, které určují typ nalezeného souboru nebo serveru. Seznam typů lokátorů gopher naleznete v tématu [GetLocatorType.](#getlocatortype)

Aplikace obvykle používá lokátor pro volání [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) k načtení určité informace.

Další informace o `CGopherLocator` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

Tato členská funkce je `CGopherLocator` volána k vytvoření objektu.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
Odkaz na konstantní `CGopherLocator` objekt.

### <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CGopherLocator` objekt přímo. Místo toho volání [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) vytvořit a `CGopherLocator` vrátit ukazatel na objekt.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType

Volání této členské funkce získat typ lokátoru.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parametry

*dwRef*<br/>
Odkaz na DWORD, který obdrží typ lokátoru. Viz **Poznámky** pro tabulku typů lokátorů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Možné typy jsou následující:

|Hodnota|Význam|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Textový soubor ASCII.|
|GOPHER_TYPE_DIRECTORY|Adresář dalších položek Gopher.|
|GOPHER_TYPE_CSO|Server telefonního seznamu CSO.|
|GOPHER_TYPE_ERROR|Označuje chybový stav.|
|GOPHER_TYPE_MAC_BINHEX|Soubor Macintosh ve formátu BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Archivní soubor DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Soubor UUENCODED.|
|GOPHER_TYPE_INDEX_SERVER|Indexový server.|
|GOPHER_TYPE_TELNET|A Telnet Server.|
|GOPHER_TYPE_BINARY|Binární soubor.|
|GOPHER_TYPE_REDUNDANT|Duplicitní server. Informace obsažené v rámci je duplikát primárního serveru. Primární server je poslední položka adresáře, která nemá typ GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Server TN3270.|
|GOPHER_TYPE_GIF|Grafický soubor GIF.|
|GOPHER_TYPE_IMAGE|Soubor obrázku.|
|GOPHER_TYPE_BITMAP|Bitmapový soubor.|
|GOPHER_TYPE_MOVIE|Filmová složka.|
|GOPHER_TYPE_SOUND|Zvukový soubor.|
|GOPHER_TYPE_HTML|Dokument HTML.|
|GOPHER_TYPE_PDF|Soubor PDF.|
|GOPHER_TYPE_CALENDAR|Soubor kalendáře.|
|GOPHER_TYPE_INLINE|Vsazený soubor.|
|GOPHER_TYPE_UNKNOWN|Typ položky není znám.|
|GOPHER_TYPE_ASK|Ask + položka.|
|GOPHER_TYPE_GOPHER_PLUS|Položka Gopher+.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::operátor LPCTSTR

Tento užitečný operátor přetypování poskytuje efektivní metodu pro přístup `CGopherLocator` k řetězci C ukončenému null obsaženému v objektu.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel znaku na data řetězce.

### <a name="remarks"></a>Poznámky

Nejsou zkopírovány žádné znaky; je vrácen pouze ukazatel.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)
