---
title: "Datum a čas: SYSTEMTIME – podpora | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 405c245cdab6426330915c945cd77f8336e68c9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="date-and-time-systemtime-support"></a>Datum a čas: SYSTEMTIME – podpora
[CTime](../atl-mfc-shared/reference/ctime-class.md) třída obsahuje konstruktory, které přijímají systému a soubor časy z Win32. Pokud používáte `CTime` objekty pro tyto účely, musíte změnit své inicializace podle toho, jak je popsáno v tomto článku.  
  
 Informace o SYSTEMTIME – struktura najdete v tématu [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Informace o struktuře FILETIME najdete v tématu [FILETIME](../mfc/reference/filetime-structure.md).  
  
 MFC stále poskytuje `CTime` konstruktory, které nepřijímají čas argumenty ve stylu MS-DOS, ale, počínaje MFC verze 3.0, `CTime` třída také podporuje konstruktor, který přebírá Win32 `SYSTEMTIME` struktura a druhou, která přebírá Win32 `FILETIME` struktury.  
  
 Nové `CTime` konstruktory jsou:  
  
-   CTime – (const SYSTEMTIME & `sysTime`);  
  
-   CTime – (const FILETIME & `fileTime`);  
  
 `fileTime` Parametr je odkaz na Win32 `FILETIME` struktury, která představuje dobu jako hodnotu 64-bit pohodlnější formát pro interní úložiště než `SYSTEMTIME` strukturu a formát používaný Win32 představují čas souboru vytvoření.  
  
 Pokud váš kód obsahuje `CTime` objekt inicializovat se systémovým časem, byste měli používat `SYSTEMTIME` konstruktor v Win32.  
  
 Pravděpodobně nebudete používat `CTime` `FILETIME` inicializace přímo. Pokud používáte `CFile` objekt, který chcete upravit soubor [CFile::GetStatus](../mfc/reference/cfile-class.md#getstatus) načte časové razítko souboru pro vás prostřednictvím `CTime` objekt inicializován s `FILETIME` struktury.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Obecné datum a čas programování v prostředí MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Podpora automatizace datum a čas programování](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [Obecné třídy pro datum a čas programování](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas](../atl-mfc-shared/date-and-time.md)

