---
title: Otevírání souborů | Microsoft Docs
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
ms.openlocfilehash: 379449469d37f01c7c0fd225688a019eaec9e977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="opening-files"></a>Otevírání souborů
V prostředí MFC je nejběžnější způsob, jak otevřít soubor dvoustupňový proces.  
  
#### <a name="to-open-a-file"></a>K otevření souboru  
  
1.  Vytvořte objekt souboru bez zadání oprávnění nebo cesta příznaky.  
  
     Obvykle vytvoříte objekt souboru deklarace [cfile –](../mfc/reference/cfile-class.md) proměnné na rámec zásobníku.  
  
2.  Volání [otevřete](../mfc/reference/cfile-class.md#open) – členská funkce objektu soubor zadávání příznaky cestu a oprávnění.  
  
     Návratovou hodnotu pro `Open` bude nenulové hodnoty, pokud soubor byl úspěšně otevřen nebo 0. Pokud nelze otevřít zadaný soubor. `Open` – Členská funkce je deklaraci následujícím způsobem:  
  
     `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`  
  
     Otevřete příznaky například zadejte, jaká oprávnění jen pro čtení, které chcete použít pro soubor. Příznak možné hodnoty jsou definovány jako konstanty výčtu v rámci `CFile` třídy, takže jsou k kvalifikovaný s "`CFile::`" jako v `CFile::modeRead`. Použití `CFile::modeCreate` příznak, pokud chcete vytvořit soubor.  
  
 Následující příklad ukazuje, jak vytvořit nový soubor s oprávněním ke čtení a zápis (nahrazení všech předchozích souboru se stejnou cestou):  
  
 [!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]  
  
> [!NOTE]
>  Tento příklad vytvoří a otevře soubor. Pokud dochází k problémům, `Open` volání můžete vrátit `CFileException` objekt v jeho poslední parametr, jak je vidět tady. `TRACE` Makro vytiskne název souboru a kód označující důvod selhání. Můžete volat `AfxThrowFileException` fungovat, pokud požadujete podrobnější zasílání zpráv o chybách.  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../mfc/reference/cfile-class.md)   
 [CFile::Open](../mfc/reference/cfile-class.md#open)   
 [Soubory](../mfc/files-in-mfc.md)

