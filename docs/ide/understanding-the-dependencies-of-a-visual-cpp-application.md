---
title: "Principy závislostí v aplikaci Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 94e1978c5c0188410cf8d6d6bfdfe08d9af620e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Principy závislostí v aplikacích Visual C++
Chcete-li zjistit, které knihovny jazyka Visual C++ aplikace závisí na, můžete zobrazit vlastnosti projektu. (V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **vlastnosti** otevřete **stránky vlastností** dialogové okno.) Můžete použít také Prohlížeč závislostí (depends.exe), který vám poskytne komplexnější přehled o závislostech v projektu.  
  
 V **stránky vlastností** dialogové okno, můžete zkontrolovat v části stránky **vlastnosti konfigurace** pochopit závislosti. Například, pokud používá projektu knihovny MFC a zvolíte **použití knihovny MFC**, **použití knihovny MFC ve sdílené knihovně DLL** na **vlastnosti konfigurace**, **obecné**  stránce aplikace za běhu závisí na MFC – knihovny DLL například mfc\<verze > .dll. Pokud vaše aplikace nepoužívá MFC, pokud si zvolíte, se může záviset na knihovny CRT **Runtime Library** hodnotu **Multi-threaded Debug DLL (/ MDd)** nebo **Multi-threaded DLL (/ MD)**na **vlastnosti konfigurace**, **C/C++**, **generování kódu** stránky.  
  
 Komplexnější způsob jak určit, které knihovny DLL, které závisí aplikace na je k otevření aplikace použít závislost Walkera (depends.exe). Si můžete stáhnout nástroj z [Walkera závislostí](http://go.microsoft.com/fwlink/p/?LinkId=132640) webu.  
  
 Pomocí depends.exe můžete zkontrolovat seznam knihoven DLL, které jsou propojeny s aplikace při načítání a seznam jeho DLL s odloženým načtením. Pokud chcete získat úplný seznam knihoven DLL, které jsou načtené dynamicky za běhu, můžete použít funkci profilování v depends.exe k testování aplikace, dokud si jisti, že byly využity všechny cesty kódu. Po ukončení relace profilování zobrazí depends.exe, které knihovny DLL byly načteny dynamicky za běhu.  
  
 Při práci s nástrojem depends.exe je třeba si uvědomit, že knihovna DLL může mít závislost na jiné knihovně DLL nebo na konkrétní verzi knihovny DLL. Nástroj depends.exe můžete použít na vývojářském nebo cílovém počítači. Na vývojářském počítači vypíše nástroj depends.exe knihovny DLL, které jsou nutné k podpoře aplikace. Máte-li potíže se spuštěním aplikace v cílovém počítači, můžete na něj zkopírovat nástroj depends.exe a aplikaci pak otevřít v něm. Tak zjistíte, zda některá z požadovaných knihoven DLL nechybí nebo není nesprávná.  
  
 Když víte, na kterých knihovnách DLL aplikace závisí, můžete určit knihovny, které je třeba distribuovat s aplikací při nasazování do jiného počítače. Ve většině případů nemusíte znovu distribuovat systémové knihovny DLL, ale možná budete muset znovu distribuovat knihovny DLL pro knihovny jazyka Visual C++. Další informace najdete v tématu [určení, které knihovny DLL znovu distribuovat](../ide/determining-which-dlls-to-redistribute.md).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)