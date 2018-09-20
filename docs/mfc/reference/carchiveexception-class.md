---
title: Carchiveexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaa395fa395b65b3d54a970c5832f165c8d4490c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421112"
---
# <a name="carchiveexception-class"></a>Carchiveexception – třída

Představuje podmínku výjimky serializace

## <a name="syntax"></a>Syntaxe

```
class CArchiveException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Vytvoří `CArchiveException` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Označuje příčina výjimky.|
|[CArchiveException::m_strFileName](#m_strfilename)|Určuje název souboru pro tuto podmínku.|

## <a name="remarks"></a>Poznámky

`CArchiveException` Třída zahrnuje data veřejného člena, který označuje důvod výjimky.

`CArchiveException` objekty jsou vytvořena a vyvolána uvnitř [CArchive](../../mfc/reference/carchive-class.md) členské funkce. Můžete přístup k těmto objektům v rámci oboru **CATCH** výrazu. Kód důvodu je nezávislé na operační systém. Další informace o zpracování výjimek naleznete v tématu [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException

Vytvoří `CArchiveException` objekt uložení hodnoty z *způsobit* v objektu.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*Příčina*<br/>
Proměnná výčtového typu, který označuje důvod výjimky. Seznam čítačů, najdete v článku [m_cause](#m_cause) datový člen.

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název `CArchive` objekt, který způsobil výjimku.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CArchiveException` objektů na haldě a vyvolat sami nebo nechat globální funkce [afxthrowarchiveexception –](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) ji zpracovat za vás.

Nepoužívejte tento konstruktor přímo. Místo toho zavolejte funkci globální `AfxThrowArchiveException`.

##  <a name="m_cause"></a>  CArchiveException::m_cause

Určuje příčina výjimky.

```
int m_cause;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je veřejná proměnná typu **int**. Jeho hodnoty jsou definovány `CArchiveException` výčtového typu. Čítačů a jejich význam jsou následující:

- `CArchiveException::none` Nedošlo k žádné chybě.

- `CArchiveException::genericException` Došlo k nespecifikované chybě.

- `CArchiveException::readOnly` Došlo k pokusu o zápis v rámci archivu otevřeného pro načtení.

- `CArchiveException::endOfFile` Dosaženo konce souboru při čtení objektu.

- `CArchiveException::writeOnly` Došlo k pokusu o čtení v rámci archivu otevřeného pro ukládání.

- `CArchiveException::badIndex` Neplatný formát souboru.

- `CArchiveException::badClass` Došlo k pokusu o čtení objektu do objektu nesprávného typu.

- `CArchiveException::badSchema` Došlo k pokusu o čtení objektu s jinou verzi třídy.

    > [!NOTE]
    >  Tyto `CArchiveException` příčina enumerátory se liší od `CFileException` způsobit enumerátory.

    > [!NOTE]
    > `CArchiveException::generic` je zastaralý. Místo nich se používá `genericException`. Pokud **obecný** se použijí v aplikaci a vytvořené s parametrem/CLR, bude chyby syntaxe, které nejsou snadno dekódovat.

##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName

Určuje název souboru pro tuto podmínku.

```
CString m_strFileName;
```

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CArchive – třída](../../mfc/reference/carchive-class.md)<br/>
[Afxthrowarchiveexception –](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Zpracování výjimek](../../mfc/reference/exception-processing.md)

