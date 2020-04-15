---
title: CGopherFile – třída
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373696"
---
# <a name="cgopherfile-class"></a>CGopherFile – třída

Poskytuje funkce pro hledání a čtení souborů na serveru gopher.

> [!NOTE]
> Třídy `CGopherConnection` `CGopherFile`, `CGopherFileFind` `CGopherLocator` , a jejich členové byly zastaralé, protože nefungují na platformě systému Windows XP, ale budou pokračovat v práci na dřívějších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|Vytvoří `CGopherFile` objekt.|

## <a name="remarks"></a>Poznámky

Služba gopher neumožňuje uživatelům zapisovat data do souboru gopher, protože tato služba funguje hlavně jako rozhraní řízené nabídkou pro vyhledávání informací. Členské `CGopherFile` funkce `Write` `WriteString`, `Flush` a nejsou `CGopherFile`implementovány pro . Volání těchto funkcí `CGopherFile` na objekt, vrátí [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Další informace o `CGopherFile` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor CStdio](../../mfc/reference/cstdiofile-class.md)

[Soubor CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopherFile::CGopherFile

Tato členská funkce je `CGopherFile` volána k vytvoření objektu.

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

*hSoubor*<br/>
Popisovač souboru HINTERNET.

*refLocator*<br/>
Odkaz na objekt [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*pPřipojení*<br/>
Ukazatel na objekt [CGopherConnection.](../../mfc/reference/cgopherconnection-class.md)

*hRelace*<br/>
Popisovač aktuální relace Internetu.

*pstrLocator*<br/>
Ukazatel na řetězec používaný k vyhledání serveru gopher. Další informace o lokátorech gopher naleznete v tématu [Gopher Sessions.](cgopherlocator-class.md)

*dwLocLen*<br/>
DWORD obsahující počet bajtů v *pstrLocator*.

*dwKontext*<br/>
Ukazatel na identifikátor kontextu souboru, který se otevírá.

### <a name="remarks"></a>Poznámky

Potřebujete `CGopherFile` objekt ke čtení ze souboru během relace gopher Internet.

Nikdy nevytváříte `CGopherFile` objekt přímo. Místo toho zavolejte [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) a otevřete soubor na serveru gopher.

## <a name="see-also"></a>Viz také

[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)<br/>
[Třída CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[Třída CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
