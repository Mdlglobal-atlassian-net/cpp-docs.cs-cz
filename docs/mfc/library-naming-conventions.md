---
title: "Konvence vytváření názvů knihoven | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NAFXCW.LIB [MFC]
- libraries [MFC], static
- coding conventions [MFC], MFC library names
- NAFXCWD.LIB [MFC]
- console applications [MFC], MFC library versions
- naming conventions [MFC], MFC object code libraries
- object code libraries, MFC naming conventions
- object code libraries
- conventions [MFC], MFC library names
- MFC libraries, naming conventions
ms.assetid: 39fe7d93-5a14-4c6a-b16c-bf318fa01278
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fd3a4464a7857a3fecac040be7b9d4f1161b4a37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="library-naming-conventions"></a>Zásady vytváření názvů knihoven
Kód objektu knihovny MFC použijte následující zásady vytváření názvů. Názvy knihoven mají tvar  
  
 *u*afx –*c*W*d*. LIB  
  
 zobrazených kurzívou malá písmena, kde jsou zástupné symboly specifikátory jejichž významy jsou uvedeny v následující tabulce:  
  
### <a name="library-naming-conventions"></a>Zásady vytváření názvů knihoven  
  
|Specifikátor|Hodnoty a významy|  
|---------------|-------------------------|  
|*u*|ANSI (ne) nebo Unicode (U)|  
|*c*|Typ programu, který chcete vytvořit: C = all|  
|*d*|Ladění a vydání: D = Debug; vynechat – specifikátor pro vydání|  
  
 Ve výchozím nastavení se sestavení ladění aplikací Windows ANSI pro platformu Intel: NAFXCWD.Lib. Všechny knihovny uvedené v následující tabulce jsou zahrnuty v adresáři \atlmfc\lib předem.  
  
### <a name="static-link-library-naming-conventions"></a>Staticky propojené knihovny konvence vytváření názvů  
  
|Knihovna|Popis|  
|-------------|-----------------|  
|NAFXCW.LIB|Staticky propojené knihovny MFC, prodejní verze|  
|NAFXCWD.LIB|Staticky propojené knihovny MFC, ladicí verze|  
|UAFXCW. LIB|Staticky propojené knihovny MFC s podporou Unicode, prodejní verze|  
|UAFXCWD. LIB|Staticky propojené knihovny MFC s podporou Unicode ladicí verze|  
  
> [!NOTE]
>  Pokud potřebujete k vytváření knihovní verze, najdete v souboru Readme.Txt v adresáři \atlmfc\src\mfc. Tento soubor popisuje pomocí zadané souboru pravidel NMAKE.  
  
 Další informace najdete v tématu [zásady vytváření názvů pro knihovny MFC DLL](../build/naming-conventions-for-mfc-dlls.md) a [Unicode verze knihovny MFC](../mfc/unicode-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Verze knihovny MFC](../mfc/mfc-library-versions.md)

