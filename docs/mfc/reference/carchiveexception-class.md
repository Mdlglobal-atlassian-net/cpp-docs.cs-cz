---
title: CArchiveException – třída
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855278"
---
# <a name="carchiveexception-class"></a>CArchiveException – třída

Představuje podmínku výjimky serializace.

## <a name="syntax"></a>Syntaxe

```
class CArchiveException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Vytvoří objekt `CArchiveException`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CArchiveException:: m_cause](#m_cause)|Určuje příčinu výjimky.|
|[CArchiveException:: m_strFileName](#m_strfilename)|Určuje název souboru pro tuto podmínku výjimky.|

## <a name="remarks"></a>Poznámky

Třída `CArchiveException` zahrnuje veřejný datový člen, který určuje příčinu výjimky.

objekty `CArchiveException` jsou vytvářeny a vyvolány uvnitř členských funkcí [CArchive](../../mfc/reference/carchive-class.md) . K těmto objektům máte přístup v rámci rozsahu výrazu **catch** . Kód příčiny nezávisí na operačním systému. Další informace o zpracování výjimek naleznete v tématu [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CException –](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="carchiveexception"></a>CArchiveException::CArchiveException

Vytvoří objekt `CArchiveException` a uloží hodnotu *příčiny* do objektu.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*způsobit*<br/>
Proměnná výčtového typu, která určuje důvod výjimky. Seznam enumerátorů naleznete v tématu [m_cause](#m_cause) data member.

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název objektu `CArchive`, který způsobil výjimku.

### <a name="remarks"></a>Poznámky

V haldě můžete vytvořit objekt `CArchiveException` a vyvolat ho sami nebo nechat globální funkce [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) ho zpracovat za vás.

Nepoužívejte tento konstruktor přímo; místo toho zavolejte globální funkci `AfxThrowArchiveException`.

##  <a name="m_cause"></a>CArchiveException:: m_cause

Určuje příčinu výjimky.

```
int m_cause;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je veřejná proměnná typu **int**. Jeho hodnoty jsou definovány výčtovým typem `CArchiveException`. Enumerátory a jejich významy jsou následující:

- `CArchiveException::none` nedošlo k žádné chybě.

- `CArchiveException::genericException` nespecifikovanou chybou.

- `CArchiveException::readOnly` se pokusil zapisovat do archivu otevřeného pro načtení.

- Při čtení objektu `CArchiveException::endOfFile` dosaženo konce souboru.

- `CArchiveException::writeOnly` se pokusilo číst z archivu otevřeného pro ukládání.

- `CArchiveException::badIndex` neplatný formát souboru.

- `CArchiveException::badClass` se pokusil přečíst objekt do objektu nesprávného typu.

- `CArchiveException::badSchema` se pokusil přečíst objekt s jinou verzí třídy.

    > [!NOTE]
    >  Tyto `CArchiveException` způsobují, že enumerátory jsou odlišné od `CFileException` způsobujících výčty.

    > [!NOTE]
    > `CArchiveException::generic` je zastaralá. Místo toho použijte `genericException`. Pokud je v aplikaci použito **Obecné** a sestavené s možností/CLR, dojde k chybám syntaxe, které nelze snadno dešifrovat.

##  <a name="m_strfilename"></a>CArchiveException:: m_strFileName

Určuje název souboru pro tuto podmínku výjimky.

```
CString m_strFileName;
```

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CArchive – třída](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Zpracování výjimek](../../mfc/reference/exception-processing.md)
