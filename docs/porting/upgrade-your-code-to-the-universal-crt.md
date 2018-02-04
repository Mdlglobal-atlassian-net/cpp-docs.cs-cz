---
title: "Upgrade kódu na Universal CRT | Microsoft Docs"
ms.custom: 
ms.date: 03/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e63945dc51fe55d81963790e7373a3d4dc9b0efe
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Upgrade kódu na Universal CRT

V sadě Visual Studio 2015 se rozdělili Microsoft C Runtime Library (CRT). Standardní knihovny jazyka C, POSIX rozšíření a specifické pro společnost Microsoft funkcích, makra a globální proměnné byly přesunuty do nové knihovny, Universal běhové knihovny jazyka C (Universal CRT nebo UCRT). Kompilátoru konkrétní součástí CRT byly přesunuty do nové knihovny vcruntime.  
  
UCRT je teď součástí Windows a dodává jako součást Windows 10. UCRT podporuje stabilní ABI podle konvence volání jazyka C a vyhovuje úzce standardní jenom na několik výjimek ISO C99. Je už je vázaný na konkrétní verzi kompilátoru. Můžete UCRT na libovolnou verzi systému Windows nepodporuje Visual Studio 2015 nebo Visual Studio 2017. Výhodou je, že už muset aktualizovat vaše sestavení pro cílení na novou verzi CRT při každém upgradu sady Visual Studio.  
  
Pomocí této refaktoring změnily názvy nebo umístění mnoho CRT hlavičkových souborů, soubory knihovny a redistributables a metody nasazení, vyžaduje se pro váš kód. Kromě toho mnoha funkcemi a makry v UCRT byly přidat nebo změnit tak, aby zlepšit standardy shoda. Abyste mohli využívat tyto změny, se musí aktualizovat stávající kód a systémy sestavení projektu.  
  
## <a name="where-to-find-the-universal-crt-files"></a>Kde se mají hledat soubory Universal CRT

Jako Windows jsou teď součástí Windows software development kit (SDK) komponenty, soubory UCRT knihovny a hlavičky. Při instalaci sady Visual Studio jsou nainstalovány také součástí sady Windows SDK k použití UCRT vyžaduje. Instalační program sady Visual Studio přidá umístění UCRT hlavičky, knihovny a soubory DLL k výchozím cestám používané projekt Visual Studio sestavení systému. Když aktualizujete projekty Visual C++, pokud používají výchozí nastavení projektu, rozhraní IDE automaticky vyhledá nová umístění pro soubory hlaviček a linkeru automaticky použije nový výchozí UCRT a vcruntime knihovny. Podobně pokud pomocí příkazového řádku vývojáře provádět sestavení příkazového řádku, prostředí, ve kterém jsou aktualizovány proměnné, které obsahují cesty pro knihovny a hlavičky a pracovní i automaticky.  
  
Soubory hlaviček standardní knihovny jazyka C se nyní nacházejí ve Windows SDK ve složce zahrnutí v adresáři specifické pro verzi služby SDK. Typické umístění pro soubory hlaviček je Program Files nebo adresář Program Files (x86) v rámci sady Windows\\10\\zahrnout\\_verze sady sdk_\\ucrt, kde _verze sady sdk_ odpovídá verzi systému Windows nebo aktualizace, například 10.0.14393.0 pro 10 Anniversary aktualizace systému Windows.   
  
Statické knihovny UCRT a dynamické knihovny se zakázaným inzerováním se nacházejí v Program Files nebo adresář Program Files (x86) v rámci sady Windows\\10\\Lib\\_verze sady sdk_\\ucrt \\ _architektura_, kde _architektura_ je ARM, x 86 nebo X64. Statické knihovny maloobchodní a ladění jsou libucrt.lib a libucrtd.lib a knihovny pro knihovny DLL UCRT ucrt.lib a ucrtd.lib.  
  
Maloobchodní a ladění knihoven DLL UCRT se nacházejí v různých místech. Prodejní verze knihovny DLL jsou distribuovatelné a najdete v souborech programu nebo adresář Program Files (x86) v rámci sady Windows\\10\\Redist\\ucrt\\knihovny DLL\\_architektura_\. Ladění UCRT knihovny nejsou redistributable a nachází se v Program Files nebo adresář Program Files (x86) v rámci sady Windows\\10\\bin\\_architektura_\\ucrt složka.   

C a C++ runtime kompilátoru konkrétní podpory knihovny, **vcruntime**, obsahuje kód potřebné k podpoře spuštění programu a funkce, jako je například zpracování výjimek a vnitřní funkce. Knihovnu a její soubory hlaviček se stále nacházejí ve složce Microsoft Visual Studio specifické pro verzi v Program Files nebo adresář programových souborů (x86). Ve Visual Studio 2017 hlavičky se nacházejí v rámci sady Microsoft Visual Studio\\2017\\_edition_\\VC\\nástroje\\MSVC\\  _lib – verze_\\zahrnout a knihovny DLL se nacházejí v rámci sady Microsoft Visual Studio\\2017\\_edition_\\VC\\nástroje \\MSVC\\_lib-version_\\lib\\_architektura_, kde _edice_ závisí na edici sady Visual Studio nainstalována _lib-version_ je verze knihoven, a _architektura_ je na architektuře procesoru. Knihovny DLL pro OneCore a úložišti se také nacházejí ve složce knihovny. Ladění a prodejní verze se statickou knihovnou jsou libvcruntime.lib a libvcruntimed.lib. Dynamické knihovny se zakázaným inzerováním maloobchodní a ladění jsou vcruntime.lib a vcruntimed.lib, v uvedeném pořadí.  
  
Pokud aktualizujete projekty Visual C++, pokud jste nastavili projektu **Linkeru** vlastnost **ignorovat všechny výchozí knihovny** k **Ano** nebo pokud používáte /NODEFAULTLIB linkeru Možnosti na příkazovém řádku a potom musíte aktualizovat seznam knihovny, které chcete zahrnout do nové, rozdělili knihoven. Nahraďte staré knihovny CRT, například libcmt.lib, libcmtd.lib, msvcrt.lib nebo msvcrtd.lib, ekvivalentní refactored knihovny. Informace o konkrétní knihovny použít, najdete v části [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).  
  
## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Nasazení a další šíření Universal CRT
  
Vzhledem k tomu, že UCRT je nyní součástí operačního systému Microsoft Windows, je součástí operačního systému ve Windows 10 a je k dispozici prostřednictvím služby Windows Update pro starší operační systémy Windows Vista prostřednictvím Windows 8.1. Redistributable verze je k dispozici pro systém Windows XP. Jako součást operačního systému UCRT aktualizace a údržba jsou spravovány službou Windows Update nezávisle na verze kompilátoru Visual Studio a Microsoft C++. Protože UCRT je součástí systému Windows pro zabezpečení a snadné aktualizací a menší velikost bitové kopie, důrazně doporučujeme centrální nasazení UCRT pro vaši aplikaci.  
  
Můžete UCRT na libovolnou verzi systému Windows nepodporuje Visual Studio 2015 nebo Visual Studio 2017. Můžete znovu distribuovat pomocí balíčku pro balíček vcredist pro podporované verze systému Windows než Windows 10. Balíčky vcredist zahrnout UCRT součásti a automaticky nainstalovány v operačních systémech Windows, které nemají je ve výchozím nastavení nainstalovaná. Další informace najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
Místní aplikace nasazení UCRT je podporováno, když není doporučeno z důvodů výkonu a zabezpečení. Knihovny DLL pro místní aplikace nasazení jsou zahrnuty v rámci sady Windows SDK, v části **redist** podadresáři. Knihovny DLL požadované zahrnují ucrtbase.dll a sadu **APISet předávání** knihovny DLL s názvem rozhraní api-ms-win -_podmnožina_.dll. Sada knihoven DLL vyžaduje na všech operačních systémech liší, proto doporučujeme zahrnete všechny knihovny DLL při použití aplikace místní nasazení. Upozornění o nasazení místní aplikace a další podrobnosti najdete v tématu [nasazení v jazyce Visual C++](../ide/deployment-in-visual-cpp.md).  
  
## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Změny Universal CRT funkcemi a makry  

Mnoho funkcí byly přidány nebo aktualizovány v UCRT ke zlepšení ISO C99 shoda a řeší problémy kvality a zabezpečení kódu. V některých případech to vyžaduje nejnovější změny do knihovny. Pokud váš kód zkompilovat řádně při použití starší verze CRT ale zalomení při kompilování v UCRT, musíte změnit svůj kód využít výhod těchto aktualizací a funkcí. Podrobný seznam možností nejnovější změny a aktualizace CRT najít v Universal CRT, najdete v článku [C Runtime Library (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) historie změn části Visual C++. Obsahuje seznam ovlivněných hlavičky a funkce, které můžete použít k identifikaci změny potřebné v kódu.  
  
## <a name="see-also"></a>Viz také  

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)  
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)  
[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)  
