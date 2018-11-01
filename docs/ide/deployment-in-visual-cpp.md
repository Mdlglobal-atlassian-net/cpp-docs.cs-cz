---
title: Nasazení ve Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 7ca65acef2395bca370aba9b6e435d3f3a152148
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568473"
---
# <a name="deployment-in-visual-c"></a>Nasazení ve Visual C++

Instalace aplikace na jiném počítači než vývojovém počítači se označuje jako *nasazení*. Při nasazení aplikace Visual C++ do jiného počítače, je nutné nainstalovat aplikace a všechny soubory knihoven, na kterých závisí. Visual Studio umožňuje tři způsoby nasazení knihoven Visual C++ spolu s aplikací: *centrální nasazení*, *místní nasazení*, a *statické propojování*. Centrální nasazení umístí soubory knihovny v adresáři Windows, kde služba Windows Update můžete je aktualizovat automaticky. Místní nasazení umístí soubory s knihovny ve stejném adresáři jako vaši aplikaci. Je nutné znovu nasadit všechny místně nasazených knihoven sami je aktualizovat. Statické propojení váže kód knihovny do vaší aplikace. Musíte znovu zkompilovat a znova nasazovat aplikaci, abyste mohli využívat všechny aktualizace do knihoven při použití statické propojování.

Knihovna Runtime jazyka C společnosti Microsoft se v sadě Visual Studio 2015, teď vyčleněný do místní knihovní verze konkrétní součásti a nové, která je teď součástí sady Windows Universal C Runtime knihovny. Podrobnosti o nasazení na Universal CRT naleznete v tématu [Universal CRT nasazení](universal-crt-deployment.md).

## <a name="central-deployment"></a>Centrální nasazení

Při centrálním nasazení jsou nainstalovány soubory knihovny DLL ve složce Windows\System32 nebo souborů knihoven 32-bit na x64 systémy, Windows\SysWow64 adresáře. Společnost Microsoft automaticky aktualizuje knihovny, které jsou nasazeny centrálně. Pro knihovny Visual C++, které jsou nasazeny místně nebo staticky propojeny musí aktualizace zajistit.

K centrálnímu nasazení knihoven Visual C++, slouží jedna z těchto dvou zdrojů pro soubory k instalaci:

- *Distribuovatelný balíček* soubory, které jsou samostatné spustitelné soubory příkazového řádku, které obsahují všechny knihovny Visual C++ redistributable v komprimované formě, nebo

- *Distribuovatelné slučovací moduly* (soubory .msm), který můžete použít k nasazení konkrétních knihoven a které zahrnete do souboru Instalační služby systému Windows (.msi) vaší aplikace.

Soubor distribuovatelného balíčku nainstaluje všechny knihovny Visual C++ pro určitou architekturu systému. Například pokud vaše aplikace je sestavená pro x64, můžete použít Distribuovatelný balíček vcredist_x64.exe k instalaci všech knihoven Visual C++, které vaše aplikace používá. Můžete naprogramovat instalačním programem vaší aplikace ke spuštění Distribuovatelný balíček rozhraní jako předpoklad před instalací aplikace.

Slučovací modul umožňuje zařadit logiku nastavení pro konkrétní knihovnu Visual C++ v souboru instalačního programu aplikace Instalační služby systému Windows. Mohou obsahovat libovolný počet nebo jako několik slučovací moduly, jak vaše aplikace vyžaduje. Používejte slučovací moduly, když budete chtít pro minimalizaci velikosti vašeho nasazení binárních souborů.

Protože centrální nasazení pomocí distribuovatelných balíčků nebo slučovací moduly povolí Windows Update k automatické aktualizaci knihoven Visual C++, doporučujeme použít knihovnu DLL ve vaší aplikaci místo statické knihovny a použít centrální nasazení místo místního nasazení.

## <a name="local-deployment"></a>Místní nasazení

V místním nasazení se soubory knihovny nainstalují do složky aplikace spolu se spustitelným souborem. Různé verze knihoven Visual C++ redistributable můžete nainstalovat ve stejné složce, protože název souboru každé verze obsahuje číslo verze. Například verze 12 prostředí runtime knihoven jazyka C++ je msvcp120.dll a verze 14 je msvcp140.dll.

Knihovny může rozděleny mezi několik dalších knihoven DLL, označované jako *dot knihovny*. Například některé funkce ve standardní knihovně vydané v sadě Visual Studio 2017 verze 15.6 byl přidán do msvcp140_1.dll, chcete-li zachovat kompatibilitu ABI msvcp140.dll. Pokud používáte Visual Studio 2017 verze 15.6 (sada nástrojů 14.13 –) nebo novější sadu nástrojů ze sady Visual Studio 2017, budete muset místně nasadit tyto knihovny tečkou, stejně jako hlavní knihovny. Tyto samostatné tečkou knihovny jsou zahrnuté do další hlavní verze základní knihovny, pak při změně ABI.

Vzhledem k tomu, že Microsoft nemůže automaticky místně aktualizace nasazení knihoven Visual C++, nedoporučujeme místní nasazení těchto knihoven. Pokud se rozhodnete použít místní nasazení distribuovatelných knihoven, doporučujeme implementovat vlastní metodu automatických aktualizací místně nasazených knihoven.

## <a name="static-linking"></a>Statické propojení

Kromě dynamicky propojené knihovny sady Visual Studio poskytuje většinu knihovny jako statických knihoven. Můžete staticky propojit statické knihovny, který je pro vaši aplikaci, propojení knihovny kódu objektu přímo do aplikace. Tím se vytvoří jediné binární hodnoty bez závislosti knihoven DLL, takže je nebudete muset nasazovat soubory knihoven Visual C++ samostatně. Však nedoporučujeme tento přístup protože staticky propojené knihovny nelze aktualizovat na místě. Pokud používáte statické propojení a potřebujete propojené knihovny aktualizovat, je nutné aplikaci znovu zkompilovat a opětovně nasadit.

## <a name="troubleshooting-deployment-issues"></a>Řešení potíží s nasazení

Pořadí načítání knihoven Visual C++ je závislé na systému. Chcete-li diagnostikovat problémy zavaděče, použijte nástroj depends.exe nebo where.exe. Další informace najdete v tématu [pořadí hledání knihoven DLL (Windows)](/windows/desktop/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Viz také:

- [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Univerzální nasazení CRT](universal-crt-deployment.md)
