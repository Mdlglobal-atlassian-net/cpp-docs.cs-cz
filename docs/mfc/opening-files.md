---
title: Otevírání souborů
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: 6119bf922b05c30a14d8421800e3931c4a038779
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375964"
---
# <a name="opening-files"></a>Otevírání souborů

V knihovně MFC je nejběžnějším způsobem otevření souboru dvoustupňový proces.

#### <a name="to-open-a-file"></a>Otevření souboru

1. Vytvořte objekt souboru bez zadání cesty nebo příznaků oprávnění.

   Objekt souboru se obvykle vytvoří deklarováním proměnné [CFile](../mfc/reference/cfile-class.md) v rámci zásobníku.

1. Volání [Open](../mfc/reference/cfile-class.md#open) členské funkce pro objekt souboru, zadání cesty a příznaky oprávnění.

   Vrácená hodnota `Open` pro bude nenulová, pokud byl soubor úspěšně otevřen, nebo 0, pokud zadaný soubor nelze otevřít. Členská `Open` funkce je prototypována takto:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Otevřené příznaky určují, která oprávnění, například jen pro čtení, chcete pro soubor. Možné hodnoty příznaku jsou definovány jako konstanty ve výčtu v rámci `CFile` třídy, takže jsou kvalifikovány "`CFile::`" jako v `CFile::modeRead`. Příznak `CFile::modeCreate` použijte, pokud chcete soubor vytvořit.

Následující příklad ukazuje, jak vytvořit nový soubor s oprávněním ke čtení a zápisu (nahrazení předchozího souboru stejnou cestou):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> Tento příklad vytvoří a otevře soubor. Pokud dojde k `Open` potížím, `CFileException` volání může vrátit objekt v jeho poslední parametr, jak je znázorněno zde. Makro TRACE vytiskne název souboru i kód označující důvod selhání. Funkci můžete `AfxThrowFileException` volat, pokud požadujete podrobnější hlášení chyb.

## <a name="see-also"></a>Viz také

[CFile – třída](../mfc/reference/cfile-class.md)<br/>
[CFile::Otevřít](../mfc/reference/cfile-class.md#open)<br/>
[Soubory](../mfc/files-in-mfc.md)
