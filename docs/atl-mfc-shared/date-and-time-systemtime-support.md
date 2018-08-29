---
title: 'Datum a čas: podpora SYSTEMTIME | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0698dbcb27e471218c39517676654156634aa022
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131383"
---
# <a name="date-and-time-systemtime-support"></a>Datum a čas: podpora SYSTEMTIME
[CTime](../atl-mfc-shared/reference/ctime-class.md) třída má konstruktory, které přijímají systému a soubor dobu od Win32. Pokud používáte `CTime` objekty pro tyto účely, je nutné upravit jejich inicializace odpovídajícím způsobem, jak je popsáno v tomto článku.  
  
 Informace o SYSTEMTIME – struktura, naleznete v tématu [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Informace o FileTime – struktura, naleznete v tématu [hodnota FILETIME](../mfc/reference/filetime-structure.md).  
  
 Knihovna MFC poskytuje stále `CTime` konstruktorů, které přijímají argumenty času ve stylu zástupného kódu MS-DOS, ale, spouští se v prostředí MFC verze 3.0, `CTime` třída také podporuje konstruktor s daným počtem Win32 `SYSTEMTIME` struktury a další vlastnost, která přebírá Win32 `FILETIME` struktury.  
  
 Nové `CTime` konstruktory jsou:  
  
-   CTime – (const SYSTEMTIME & `sysTime`);  
  
-   CTime – (konstantní hodnota FILETIME & `fileTime`);  
  
 *Hodnota fileTime* parametr je odkazem na Win32 `FILETIME` struktury, která představuje čas jako hodnotu 64-bit pohodlnější formát pro interní úložiště než `SYSTEMTIME` strukturu a formát používaný čtečkou Win32 do představuje čas vytvoření souboru.  
  
 Pokud váš kód obsahuje `CTime` objekt je inicializován s systémový čas, byste měli použít `SYSTEMTIME` konstruktor v systému Win32.  
  
 Pravděpodobně nebude používat `CTime` `FILETIME` inicializace přímo. Pokud používáte `CFile` objekt pro manipulaci s souboru [CFile::GetStatus](../mfc/reference/cfile-class.md#getstatus) načte časové razítko souboru pro vás prostřednictvím `CTime` objekt inicializován s `FILETIME` struktury.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací  
  
-   [Obecné datum a čas programování v prostředí MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Podpora automatizace data a času programování](../atl-mfc-shared/date-and-time-automation-support.md)  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas](../atl-mfc-shared/date-and-time.md)

