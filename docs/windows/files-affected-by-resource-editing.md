---
title: Soubory ovlivněné úpravou prostředku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: acdf7a2915fe17cba393d14d9d287a89515695fc
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650580"
---
# <a name="files-affected-by-resource-editing"></a>Soubory ovlivněné úpravou prostředku
Prostředí sady Visual Studio spolupracuje s souborů, které jsou uvedené v následující tabulce během vaší relace úpravy prostředků.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|Resource.h|Soubor hlaviček generovaných vývojové prostředí; obsahuje definice symbolů. (Zahrnout tento soubor do správy zdrojového kódu.)|  
|Filename.APS|Binární verze aktuálního souboru skriptu prostředků; používá se pro rychlé načítání.<br /><br /> Editory prostředků přímo číst soubory .rc nebo souboru resource.h. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a soubor resource.h). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře vždy ztratí dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md). (Obvykle, nezahrnujte .aps soubor ve správě zdrojového kódu.)|  
|.rc|Soubor skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše souborem .aps při každém uložení. (Zahrnout tento soubor do správy zdrojového kódu.)|  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)