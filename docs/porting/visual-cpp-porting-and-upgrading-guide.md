---
title: "Visual C++ Průvodce přenosem a upgradováním | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba7e3f139aa9956cd9d2587522dc2d0ac1f2ff7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="visual-c-porting-and-upgrading-guide"></a>Průvodce přenosem a upgradováním Visual C++
Toto téma obsahuje Průvodce pro upgrade Visual C++ – kód. To zahrnuje získání kód, který zkompilování a spuštění správně na novější verzi nástroje, jakož i využívat výhod nového jazyka a funkcích nástroje Visual Studio. Toto téma obsahuje také informace o migraci starší verze aplikací na více moderní platformy.  
  
## <a name="reasons-to-upgrade-visual-c-code"></a>Důvody pro Upgrade Visual C++ – kód  
 Měli byste zvážit, upgrade kódu z následujících důvodů:  
  
-   Rychlejší kód z důvodu optimalizace vylepšené kompilátoru.  
  
-   Rychlejší sestavení, z důvodu vylepšení výkonu v kompilátoru sám sebe.  
  
-   Shoda lepší standardů. Visual C++ teď implementuje mnoho funkcí z nejnovějších standardů C++.  
  
-   Lepší zabezpečení. Funkce zabezpečení, jako je kontrola ochrana.  
  
### <a name="porting-your-code"></a>Portování kódu  
 Při upgradu, nejprve zvažte kódu a projekty vaší aplikace. Je vaše aplikace vytvořené s nástroji Visual Studio?  Pokud ano, identifikujte související se situací projekty.  Máte vlastní sestavovací skripty?  Pokud máte skripty vlastního sestavení místo použití systém sestavení sady Visual Studio, budete mít více práce uděláte v upgradu, protože nelze ušetřit čas tím, že Visual Studio aktualizovat soubory projektu a nastavení sestavení.  
  
 Formát sestavení systému a projekt souboru v sadě Visual Studio se změnil z vcbuild ve verzích až Visual Studio 2008 na MSBuild verze sady Visual Studio 2010 a vyšší. Pokud se upgrade z verze před 2010 a budete mít systém vysoce přizpůsobenou sestavení, můžete chtít provést další práci pro upgrade.  Pokud jste upgrade z produktu Visual Studio 2010 nebo novější, vašich projektů se už používá MSBuild, tak upgrade projektu a sestavení pro vaše aplikace by měla být snazší.  
  
 Pokud nepoužíváte systém sestavení sady Visual Studio, měli byste zvážit, upgradu a používání nástroje MSBuild. Pokud provádíte upgrade pomocí nástroje MSBuild, může mít jednodušší čas v budoucí aktualizace, a je jednodušší použít službám, jako je Visual Studio Online. MSBuild podporuje všechny cílové platformy, které podporuje Visual Studio.  
  
### <a name="porting-visual-studio-projects"></a>Portování projektů sady Visual Studio  
  Pokud chcete spustit upgrade projekt nebo řešení, právě otevřete řešení v nové verzi sady Visual Studio a postupujte podle výzev a spusťte upgrade je.  Při upgradu na projekt, dojde upgradu zprávu, která je také uloženy ve složce projektu jako UpgradeLog.htm. Upgrade sestava zobrazuje souhrn jaké problémy se vyskytly během procesu upgradu a některé informace o změnách, které byly provedeny nebo problémy, které nelze vyřešit automaticky.  
  
1.  Vlastnosti projektu  
  
2.  Vložené soubory  
  
3.  Kód, který už zkompilován čistě z důvodu kompilátoru shoda imrovements nebo změny v standard.  
  
4.  Kód, který využívá funkce sady Visual Studio nebo systému Windows, které již nejsou k dispozici nebo soubory hlaviček, které nejsou součástí výchozí instalace sady Visual Studio, nebo byly odebrány z produktu  
  
5.  Kód, který už zkompiluje z důvodu změn v rozhraní API, jako přejmenovat rozhraní API, změnit funkce podpisy nebo zastaralé funkce  
  
6.  Kód, který už zkompiluje z důvodu změn v diagnostice, jako je například upozornění, aby se aktivovala chybu  
  
7.  Chybami linkeru z důvodu knihovny, které byly změněny, zejména v případě, že se používá /NODEFAULTLIB.  
  
8.  Chyby za běhu nebo neočekávané výsledky z důvodu změny chování  
  
9. Chyby z důvodu chyb, které byly zavedeny v nástrojích pro. Pokud narazíte na problém nahlásit týmu Visual C++ pomocí pracovníkům podpory normální, nebo pomocí [Visual Studio zpětnou vazbu Center](http://connect.microsoft.com/VisualStudio/Feedback).  
  
 Kromě změn, které se nelze vyhnout z důvodu chyb kompilátoru některé změny jsou volitelné v upgradu, jako například:  
  
1.  Nové upozornění může znamenat, že chcete vyčistit vašeho kódu. V závislosti na konkrétní diagnostiky tím lze vylepšit přenositelnost, shoda standardů a zabezpečení vašeho kódu.  
  
2.  Můžete chtít využívat výhod novější kompilátoru funkcí, jako [/guard:cf (Povolit toku řízení Guard)](../build/reference/guard-enable-control-flow-guard.md) – možnost kompilátoru, která přidává kontroluje provádění neoprávněným kódu.  
  
3.  Může chcete aktualizovat některé kódu pro použití nové jazykové funkce, které zjednodušit kód, zlepšit výkon programy nebo aktualizujte kód a používat moderní knihovny odpovídat moderních standardů a osvědčených postupů.  
  
 Jakmile jste upgradovat a testování projektu, můžete také chtít zvažte vylepšení kód další plánování budoucí směr kódu nebo i nebyla architektuře vašeho projektu. Se zobrazí probíhající vývoji? Bude být důležité pro váš kód pro spuštění na jiných platformách?  Pokud ano, jaké platformy?  C++ je standardizovaná jazyka navrhovat s přenositelnosti a vývoj pro různé platformy v paměti a ještě kód pro mnoho aplikací systému Windows je důrazně vázaný na platformě Windows. Opravdu chcete Refaktorovat kódu, jak oddělit ty části, které jsou více svázané s platformou Windows?  
  
 Co uživatelské rozhraní?  Pokud používáte MFC, můžete chtít aktualizovat uživatelského rozhraní.  Používáte všechny novější funkce MFC, které byly zavedeny v 2008 jako Feature Pack?  Pokud chcete poskytnout novější vzhled a chování vaší aplikace bez přepisování celá aplikace, můžete zvážit pomocí rozhraní API pásu karet v prostředí MFC nebo pomocí některé z nových funkcí knihovny MFC.  
  
 Pokud chcete svůj program poskytnout uživatelské rozhraní jazyka XAML, ale nechcete použít k vytvoření aplikace pro UPW, můžete C# v grafickém subsystému WPF vytvoření vrstvy uživatelského rozhraní a refactor logika standardní C++ do knihovny DLL. Vytvoření vrstvy interoperabilitu v jazyce C + +/ CLI připojit C# s nativním kódem. Další možností je vytvořit pomocí aplikace UWP [C + +/ CX](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh699871.aspx) nebo [C + +/ WinRT](https://github.com/microsoft/cppwinrt). V systému Windows 10, můžete použít [plochy aplikace převaděč](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) do balíčku plochy aplikace jako aplikace pro UPW bez nutnosti upravit žádný kód.   
 Případně třeba Teď máte nové požadavky nebo předvídáte, třeba pro cílení na platformy kromě Windows desktop, například Windows Phone nebo zařízení se systémem Android. Může portu kód uživatelského rozhraní a knihovna uživatelského rozhraní a platformy. Pomocí těchto rozhraní uživatelského rozhraní můžete cíle více zařízení a nadále používat Visual Studio a ladicí program Visual Studio jako vývojové prostředí.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Popisuje, jak používat projektů vytvořených v dřívějších verzích systému Visual C++.|  
|[Co je nového pro Visual C++ v sadě Visual Studio 2017 RC](../what-s-new-for-visual-cpp-in-visual-studio.md)|Změny v prostředí IDE a nástrojů pro Visual Studio 2017 ze sady Visual Studio 2015|  
|[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)|Vylepšení shoda standardy z Visual Studia 2015 Visual Studio 2017|  
|[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)|Seznam všech změn ve Visual C++ knihovny a nástroje pro sestavení ze sady Visual Studio 2003 prostřednictvím 2015, které může vyžadovat změny v kódu.|  
|[Novinky Visual C++ 2003–2015](visual-cpp-what-s-new-2003-through-2015.md)|Všechny "Novinky" informace pro Visual C++ ze sady Visual Studio 2003 pomocí sady Visual Studio 2015.|  
|[Přenos knihoven třetích stran](porting-third-party-libraries.md)|Postup použití **vcpkg** nástroj příkazového řádku port starší knihovny open-source na verze kompilovat s novější modulové Visual C++.|  
|[Přenos a upgrade: Příklady a případové studie](porting-and-upgrading-examples-and-case-studies.md)|Pro tento oddíl která je součástí a upgraduje několik ukázky a aplikace jsme popsané prostředí a výsledky. Může zjistit, že čtení těchto poskytuje je můžete představu o co účastní přenos a upgrade procesu. V celém procesu, budeme zabývat tipy a triky pro upgrade a zobrazit jak konkrétní chyby jsme vyřešili.|  
|[Přenos aplikací do univerzální platformy Windows](porting-to-the-universal-windows-platform-cpp.md)|Obsahuje informace o portování kódu na Windows 10|  
|[Úvod do prostředí Visual C++ pro uživatele systému UNIX](introduction-to-visual-cpp-for-unix-users.md)|Poskytuje informace pro uživatele systému UNIX, kteří jsou nové pro aplikaci Visual C++ a chcete se s ním být produktivní.|  
|[Přenos ze systému UNIX do Win32](porting-from-unix-to-win32.md)|Popisuje možnosti migrace aplikací systému UNIX do systému Windows.|  
|[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)|Podrobně zobrazuje postup upgradu vaší spravovaných rozšíření pro C++ Syntaxe použití nové syntaxe. Další informace najdete v tématu [rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).|  
  
## <a name="see-also"></a>Viz také  
 [Visual C++](../visual-cpp-in-visual-studio.md)
