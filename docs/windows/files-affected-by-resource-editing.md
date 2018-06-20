---
title: Soubory ovlivněné úpravou prostředku | Microsoft Docs
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
ms.openlocfilehash: b165dca13e30e12e1a4fdc85056920b7c10ee586
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238653"
---
# <a name="files-affected-by-resource-editing"></a>Soubory ovlivněné úpravou prostředku
Prostředí sady Visual Studio funguje se soubory uvedené v následující tabulce během relace úpravy prostředků.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|Resource.h|Soubor hlaviček generované vývojového prostředí; obsahuje definice symbolu. (Zahrnout tento soubor do správy zdrojového kódu.)|  
|Filename.APS|Binární verzi aktuální souboru skriptu prostředků; použít pro rychlé načítání.<br /><br /> Editory prostředků nečtou soubory .rc nebo resource.h přímo. Kompilátor prostředků je zkompiluje do .aps soubory, které se spotřebovávají editory prostředků. Tento soubor je krok kompilace a ukládá jenom symbolický data. Jako normální kompilaci proces, informace, které není symbolický (například komentáře) se zahodí během kompilace. Vždy, když soubor .aps získá synchronizována se soubor, znovu vygeneruje soubor (například když uložíte, editor prostředků přepíše .rc soubor a soubor resource.h). Všechny změny prostředků sami zůstanou zahrnuté v souboru .rc, ale komentáře vždy budou ztraceny po .rc soubor se přepíše. Informace o tom, jak zachovat komentáře najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md). (Obvykle je nesmí obsahovat soubor .aps ve správě zdrojového kódu.)|  
|.rc|Souboru skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše soubor .aps při každém uložení. (Zahrnout tento soubor do správy zdrojového kódu.)|  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)