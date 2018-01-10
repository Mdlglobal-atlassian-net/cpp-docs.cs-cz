---
title: "Podporované platformy (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4080fa1bac30ac88edca33f6de32b0a6490f4341
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="supported-platforms-visual-c"></a>Podporované platformy (Visual C++)

Aplikace vytvořené s použitím [!INCLUDE[vsprvs](assembler/masm/includes/vsprvs_md.md)] je možné cílit na různých platformách, následujícím způsobem.  
  
|Operační systém|x86|x64|ARM|  
|----------------------|---------|---------|---------|  
|Windows XP|X *|X *||  
|[!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)]|X *|X *||  
|Windows Vista|X|X||  
|Windows Server 2008|X|X||  
|Windows 7|X|X||  
|Windows Server 2012 R2|X|X||  
|Windows 8|X|X|X|  
|Windows 8.1|X|X|X|  
|Windows 10|X|X|X|  
|Android **|X|X|X|  
|iOS **|X|X|X|  
|Linux ***|X|X|X|  
  
\*Můžete použít sada nástrojů platformy systému Windows XP, zahrnuté v Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012 Update 1 nebo novějším na sestavení Windows XP a [!INCLUDE[WinXPSvr](build/includes/winxpsvr_md.md)] projekty. Informace o tom, jak používat tato sada nástrojů platformy najdete v tématu [konfigurace programů pro systém Windows XP](build/configuring-programs-for-windows-xp.md). Další informace o změně sada nástrojů platformy najdete v tématu [postupy: Změna cílové architektury a sady nástrojů](build/how-to-modify-the-target-framework-and-platform-toolset.md).  
  
\*\*Můžete nainstalovat **pro vývoj mobilních řešení s jazykem C++** zatížení v instalačním programu sady Visual Studio (nebo nepovinný **Visual C++ pro vývoj pro různé platformy Mobile** součásti v instalačním programu sady Visual Studio 2015) na cíl iOS nebo Android platformy. Pokyny najdete v tématu [nainstalovat Visual C++ pro vývoj mobilních řešení pro různé platformy](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). K vytvoření kódu pro iOS, musí mít počítači Mac a splňovat další požadavky. Seznam požadavků a pokyny k instalaci najdete v tématu [instalaci a konfiguraci nástroje pro sestavení pomocí iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Můžete vytvořit x86 nebo ARM kód tak, aby odpovídala hardwaru cíl. Použití x86 konfigurace k sestavení pro simulátoru iOS, Microsoft Visual Studio Emulator for Android a některé zařízení se systémem Android. Sestavení pro zařízení s iOS a většina zařízení se systémem Android pomocí konfigurace ARM.  
  
\*\*\*Můžete nainstalovat **Linux development s jazykem C++** zatížení v instalačním programu sady Visual Studio pro cílové platformy Linux. Pokyny najdete v tématu [stáhnout, nainstalovat a nastavit zatížení Linux](linux/download-install-and-setup-the-linux-development-workload.md). Tato sada nástrojů zkompiluje vaše spustitelný soubor v cílovém počítači, můžete vytvořit pro všechny podporované architektury.  

Informace o tom, jak nastavit konfiguraci cílové platformy najdete v tématu [postupy: Konfigurace projekty Visual C++ pro cíl 64-Bit, x64 platformy](build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).  
  
## <a name="see-also"></a>Viz také  

[Funkcí v edicích sady Visual Studio a nástrojů pro Visual C++](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)   
[Začínáme](/visualstudio/ide/getting-started-with-visual-cpp-in-visual-studio)