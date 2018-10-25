---
title: Otevírání souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f74c0fdcdb8d6dfe1aced33a1c7087ecde6c89ff
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080920"
---
# <a name="opening-files"></a>Otevírání souborů

Nejběžnější způsob otevření souboru v knihovně MFC, je dvoustupňový proces.

#### <a name="to-open-a-file"></a>Pro otevření souboru

1. Vytvořte soubor objektu bez zadání příznaky cestu nebo oprávnění.

   Obvykle vytvoříte soubor objekt deklarací [cfile –](../mfc/reference/cfile-class.md) proměnné v bloku zásobníku.

1. Volání [otevřít](../mfc/reference/cfile-class.md#open) členské funkce objektu soubor zadáním cesty a oprávnění příznaky.

   Návratová hodnota pro `Open` bude nenulové, pokud soubor byl úspěšně otevřen nebo 0. Pokud zadaný soubor nelze otevřít. `Open` Členská funkce je prototypem následujícím způsobem:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Otevřít příznaky zadejte například jaká oprávnění jen pro čtení, má k souboru. Příznak možné hodnoty jsou definované jako konstanty výčtu v rámci `CFile` třídy, takže jsou kvalifikována "`CFile::`" jako v `CFile::modeRead`. Použití `CFile::modeCreate` příznak, pokud chcete vytvořit soubor.

Následující příklad ukazuje, jak vytvořit nový soubor s oprávněním pro čtení/zápis (nahrazuje jakékoli předchozí soubor se stejnou cestou):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
>  Tento příklad vytvoří a otevře soubor. Pokud dojde k problémům, se `Open` volání můžete vrátit `CFileException` objektu v jeho posledního parametru, jak je znázorněno zde. TRACE – makro vytiskne název souboru a kódem, který označuje důvod selhání. Můžete volat `AfxThrowFileException` fungovat, pokud požadujete podrobnější zpráv o chybách.

## <a name="see-also"></a>Viz také

[CFile – třída](../mfc/reference/cfile-class.md)<br/>
[CFile::Open](../mfc/reference/cfile-class.md#open)<br/>
[Soubory](../mfc/files-in-mfc.md)

