---
title: Cgopherfile – třída
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 9e5fbdcd14c0f988e894718f357d40e4b238c7c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658195"
---
# <a name="cgopherfile-class"></a>Cgopherfile – třída

Poskytuje funkce pro hledání a čtení souborů na gopher serveru.

> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členy jsou zastaralé, protože nebude fungovat na platformě Windows XP, ale budou i nadále fungovat na starší platformy.

## <a name="syntax"></a>Syntaxe

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|Vytvoří `CGopherFile` objektu.|

## <a name="remarks"></a>Poznámky

Služba gopher nedovoluje uživatelům k zápisu dat do souboru gopher, protože tato služba functions především jako nabídkou řízený rozhraní pro hledání informací. `CGopherFile` Členské funkce `Write`, `WriteString`, a `Flush` nejsou implementovány pro `CGopherFile`. Volání těchto funkcí na `CGopherFile` objektu, vrátí [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).

Další informace o tom, `CGopherFile` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cfile –](../../mfc/reference/cfile-class.md)

[Cstdiofile –](../../mfc/reference/cstdiofile-class.md)

[Cinternetfile –](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile

Tato členská funkce je volána k sestavení kompletních `CGopherFile` objektu.

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>Parametry

*hfile –*<br/>
Popisovač souboru HINTERNET.

*refLocator*<br/>
Odkaz na [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu.

*pConnection*<br/>
Ukazatel [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md) objektu.

*hSession*<br/>
Popisovač s aktuální relací Internetu.

*pstrLocator*<br/>
Ukazatel na řetězec používaná k nalezení gopher serveru. Zobrazit [Gopher relace](cgopherlocator-class.md) Další informace o gopher lokátory.

*dwLocLen*<br/>
Hodnota DWORD obsahující počet bajtů v *pstrLocator*.

*dwContext*<br/>
Ukazatel na identifikátor kontextu právě otevřený soubor.

### <a name="remarks"></a>Poznámky

Je nutné `CGopherFile` objektu určeného ke čtení ze souboru během relace gopher Internet.

Nikdy nevytvářejte `CGopherFile` objektu přímo. Namísto toho zavolejte metodu [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) otevřít soubor na gopher serveru.

## <a name="see-also"></a>Viz také

[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection – třída](../../mfc/reference/cgopherconnection-class.md)
