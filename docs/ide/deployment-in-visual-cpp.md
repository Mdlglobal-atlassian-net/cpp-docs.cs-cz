---
title: "Nasazení v jazyce Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 9/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8ae663d5371626162cf3b98c1048128a61b1e1a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="deployment-in-visual-c"></a>Nasazení ve Visual C++

Instalace aplikace na jiném počítači než vývojovém počítači se označuje jako *nasazení*. Při nasazení aplikace Visual C++ do jiného počítače, je nutné nainstalovat aplikace a všechny soubory knihovny, které závisí na. Sada Visual Studio umožňuje tři způsoby, jak nasadit knihovny jazyka Visual C++ společně s aplikací: *centrální nasazení*, *místní nasazení*, a *statické propojení*. Centrální nasazení převádí soubory knihovny v adresáři systému Windows, kde služby Windows Update můžete je aktualizovat automaticky. Místní nasazení převádí soubory knihovny ve stejném adresáři jako aplikace. Je nutné znovu nasadit všechny místně nasazené knihovny sami, abyste provedli jejich aktualizaci. Statické propojení váže knihovny kódu do své aplikace. Je nutné znovu zkompiluje a znovu nasaďte aplikace využít výhod všech aktualizací do knihoven, pokud používáte statické propojení.

## <a name="central-deployment"></a>Centrální nasazení

V Centrální nasazení, jsou nainstalované soubory knihovny DLL ve složce Windows\System32 nebo u 32-bit knihovny souborů na x64 systémy, Windows\SysWow64 adresáře. Společnost Microsoft automaticky aktualizuje knihovny, které jsou nasazeny centrálně. Pro knihovny jazyka Visual C++, které jsou místně nasazen nebo staticky propojené je nutné zadat aktualizace.

K centrálnímu nasazení knihovny jazyka Visual C++, můžete jeden z těchto dvou zdrojů pro soubory k instalaci:

- *Distribuovatelný balíček* soubory, které jsou samostatné příkazového řádku spustitelné soubory, které obsahují všechny knihovny Visual C++ redistributable v komprimované formě, nebo

- *Redistributable slučovacích modulů* (soubory .msm), který můžete použít k nasazení konkrétní knihovny, na kterou můžete zahrnout do souboru Instalační služby systému Windows (.msi) vaší aplikace.

Soubor redistribuovatelný balíček nainstaluje všechny knihovny jazyka Visual C++ pro konkrétní systém architekturu. Například pokud vaše aplikace je sestavena pro x64, můžete použít vcredist_x64.exe redistribuovatelný balíček k instalaci všech knihoven Visual C++, které vaše aplikace používá. Instalační program aplikace spustit redistribuovatelného balíčku jako předpoklad před instalací aplikace můžete programu.

Modul sloučení umožňuje zahrnutí logiku nastavení pro konkrétní knihovny Visual C++ v souboru Instalační program aplikace Instalační služby systému Windows. Můžete zahrnout tolik nebo jako několik modulů sloučení vyžaduje vaše aplikace. Slučovací moduly použijte, pokud je potřeba minimální velikost vašeho nasazení binárních souborů.

Vzhledem k tomu centrální nasazení s použitím redistribuovatelného balíčku nebo slučovacích modulů umožňuje Windows Update k automatické aktualizaci knihovny jazyka Visual C++, doporučujeme, abyste pomocí knihovny DLL ve vaší aplikaci místo statických knihoven a použít centrální nasazení namísto místního nasazení.

## <a name="local-deployment"></a>Místní nasazení

V místním nasazení jsou nainstalovány knihovny soubory ve složce aplikace společně s spustitelný soubor. Různé verze knihoven Visual C++ redistributable lze nainstalovat ve stejné složce, protože název souboru jednotlivých verzí zahrnuje jeho číslo verze. Například verze 12 běhové knihovny jazyka c je msvcp120.dll a verze 14 je msvcp140.dll.

Vzhledem k tomu, že Microsoft nelze automaticky místně aktualizace nasazena knihovny jazyka Visual C++, nedoporučujeme místní nasazení tyto knihovny. Pokud se rozhodnete použít místní nasazení distribuovatelných knihoven, doporučujeme implementovat vlastní metodu automatických aktualizací místně nasazených knihoven.

## <a name="static-linking"></a>Statické propojení

Kromě dynamicky propojené knihovny Visual Studio poskytuje většinu jeho knihovny jako statické knihovny. Můžete staticky statické knihovny propojit vaší aplikace, který je, propojte objekt kód knihovny přímo do aplikace. Tím se vytvoří jediné binární bez závislosti knihovny DLL, takže není nutné nasadit knihovny souborů Visual C++ samostatně. Však není doporučeno tento přístup protože staticky propojené knihovny nelze aktualizovat na místě. Pokud používáte statické propojení a potřebujete propojené knihovny aktualizovat, je nutné aplikaci znovu zkompilovat a opětovně nasadit.

## <a name="troubleshooting-deployment-issues"></a>Nasazení řešení potíží

Pořadí načítání knihoven Visual C++ je závislá na systému. Chcete-li diagnostikovat problémy zavaděče, použijte nástroj depends.exe nebo where.exe. Další informace najdete v tématu [pořadí hledání knihovny DLL (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

## <a name="see-also"></a>Viz také

[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)