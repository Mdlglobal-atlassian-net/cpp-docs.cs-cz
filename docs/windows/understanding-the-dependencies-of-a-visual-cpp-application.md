---
title: Principy závislostí v aplikacích Visual C++
ms.date: 11/04/2016
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
ms.openlocfilehash: 92db11778de7d31bbab67e649cd58e264da331e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387848"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Principy závislostí v aplikacích Visual C++

Chcete-li zjistit, které knihovny Visual C++ aplikace závisí, můžete zobrazit vlastnosti projektu. (V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **vlastnosti** otevřít **stránky vlastností** dialogové okno.) V systému Windows 8 a dříve můžete použít také prohlížeč závislostí (depends.exe), která poskytne komplexnější přehled o závislostech. Více aktuálních verzí systému Windows [lucasg/závislosti](https://github.com/lucasg/Dependencies) nástroj poskytuje podobné funkce jako (jedná se o nástroj třetí strany, není zaručeno, že společnost Microsoft.)

V **stránky vlastností** dialogovém okně můžete zkoumáním stránek v rámci **vlastnosti konfigurace** přehled o závislostech. Například, pokud váš projekt používá knihovny MFC a zvolíte **použít knihovnu MFC**, **použít knihovnu MFC ve sdílené knihovně DLL** na **vlastnosti konfigurace**, **obecné**  stránky, vaše aplikace v době běhu závisí na knihovnách MFC DLL například knihovny mfc\<verze > .dll. Pokud vaše aplikace nepoužívá knihovnu MFC, pokud se rozhodnete, ho může záviset na knihovně CRT **knihovny prostředí Runtime** hodnotu **Multi-threaded ladit knihovnu DLL (/ MDd)** nebo **Multi-threaded DLL (/ MD)** na **vlastnosti konfigurace**, **C/C++**, **generování kódu** stránky.

Pomocí depends.exe můžete prohlížet seznam knihoven DLL, které jsou propojeny s aplikací v okamžiku načtení a seznam jeho odloženě zaváděné knihovny DLL. Pokud chcete získat úplný seznam knihoven DLL, které se načítají dynamicky za běhu, můžete použít funkce profilování v depends.exe aplikaci otestovat, dokud si jisti, že byly využity všechny cesty kódu. Po ukončení relace profilování depends.exe zobrazí, které knihovny DLL byly dynamicky načteny za běhu.

Při práci s nástrojem depends.exe je třeba si uvědomit, že knihovna DLL může mít závislost na jiné knihovně DLL nebo na konkrétní verzi knihovny DLL. Nástroj depends.exe můžete použít na vývojářském nebo cílovém počítači. Na vývojářském počítači vypíše nástroj depends.exe knihovny DLL, které jsou nutné k podpoře aplikace. Máte-li potíže se spuštěním aplikace v cílovém počítači, můžete na něj zkopírovat nástroj depends.exe a aplikaci pak otevřít v něm. Tak zjistíte, zda některá z požadovaných knihoven DLL nechybí nebo není nesprávná.

Když víte, na kterých knihovnách DLL aplikace závisí, můžete určit knihovny, které je třeba distribuovat s aplikací při nasazování do jiného počítače. Ve většině případů není nutné znovu distribuovat systémové knihovny DLL, ale možná budete muset distribuovat knihovny DLL pro knihovny Visual C++. Další informace najdete v tématu [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md).

## <a name="see-also"></a>Viz také:

[Nasazení aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)
