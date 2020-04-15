---
title: Třída CArchiveException
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
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377017"
---
# <a name="carchiveexception-class"></a>Třída CArchiveException

Představuje podmínku výjimky serializace.

## <a name="syntax"></a>Syntaxe

```
class CArchiveException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Vytvoří `CArchiveException` objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Označuje příčinu výjimky.|
|[CArchiveException::m_strFileName](#m_strfilename)|Určuje název souboru pro tuto podmínku výjimky.|

## <a name="remarks"></a>Poznámky

Třída `CArchiveException` obsahuje veřejný datový člen, který označuje příčinu výjimky.

`CArchiveException`objekty jsou konstruovány a vyvolány uvnitř funkcí členů [CArchive.](../../mfc/reference/carchive-class.md) K těmto objektům můžete přistupovat v rámci výrazu **CATCH.** Kód příčiny je nezávislý na operačním systému. Další informace o zpracování výjimek naleznete v [tématu Zpracování výjimek (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Vytvoří `CArchiveException` objekt a uváží hodnotu *příčiny* v objektu.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*Způsobit*<br/>
Ve výčtu typ proměnné, která označuje důvod výjimky. Seznam čítačů výčtu naleznete v [m_cause](#m_cause) datový člen.

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název `CArchive` objektu, který způsobuje výjimku.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CArchiveException` objekt na haldě a hodit sami nebo nechat globální funkce [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) zpracovat za vás.

Nepoužívejte tento konstruktor přímo; místo toho zavolejte `AfxThrowArchiveException`globální funkci .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException::m_cause

Určuje příčinu výjimky.

```
int m_cause;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je veřejná proměnná typu **int**. Jeho hodnoty jsou `CArchiveException` definovány ve výčtu typu. Čítači výčtu a jejich význam jsou následující:

- `CArchiveException::none`Nedošlo k žádné chybě.

- `CArchiveException::genericException`Nespecifikovaná chyba.

- `CArchiveException::readOnly`Pokusil se zapsat do archivu otevřeného pro načtení.

- `CArchiveException::endOfFile`Při čtení objektu bylo dosaženo konce souboru.

- `CArchiveException::writeOnly`Snažil se číst z archivu otevřeného pro ukládání.

- `CArchiveException::badIndex`Neplatný formát souboru.

- `CArchiveException::badClass`Došlo k pokusu o čtení objektu do objektu nesprávného typu.

- `CArchiveException::badSchema`Pokusili jste se přečíst objekt s jinou verzí třídy.

    > [!NOTE]
    >  Tyto `CArchiveException` příčiny výčtu se `CFileException` liší od čítače výčtu příčiny.

    > [!NOTE]
    > `CArchiveException::generic`je zastaralé. Místo toho použijte `genericException`. Pokud **obecný** se používá v aplikaci a je postaven s /clr, bude syntaxe chyby, které není snadné rozluštit.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException::m_strFileName

Určuje název souboru pro tuto podmínku výjimky.

```
CString m_strFileName;
```

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CArchiv](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Zpracování výjimek](../../mfc/reference/exception-processing.md)
