---
title: Soubory ovlivněné úpravou prostředku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cb103ac098c8d73db132cdb67b6ab6902ee3f591
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="files-affected-by-resource-editing"></a>Soubory ovlivněné úpravou prostředku
Prostředí sady Visual Studio funguje se soubory uvedené v následující tabulce během relace úpravy prostředků.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|Resource.h|Soubor hlaviček generované vývojového prostředí; obsahuje definice symbolu.|  
|Filename.APS|Binární verzi aktuální souboru skriptu prostředků; použít pro rychlé načítání.<br /><br /> Editory prostředků nečtou soubory .rc nebo resource.h přímo. Kompilátor prostředků je zkompiluje do .aps soubory, které se spotřebovávají editory prostředků. Tento soubor je krok kompilace a ukládá jenom symbolický data. Jako normální kompilaci proces, informace, které není symbolický (například komentáře) se zahodí během kompilace. Vždy, když soubor .aps získá synchronizována se soubor, znovu vygeneruje soubor (například když uložíte, editor prostředků přepíše .rc soubor a soubor resource.h). Všechny změny prostředků sami zůstanou zahrnuté v souboru .rc, ale komentáře vždy budou ztraceny po .rc soubor se přepíše. Informace o tom, jak zachovat komentáře najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).|  
|.rc|Souboru skriptu prostředků, který obsahuje skript pro prostředky v aktuálním projektu. Tento soubor se přepíše soubor .aps při každém uložení.|  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)