---
title: Upgrade kódu na Universal CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/31/2017
ms.topic: conceptual
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1091a28448aa6531aa909117e0284e19bbcc7cd8
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42464613"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Upgrade kódu na Universal CRT

V sadě Visual Studio 2015 se Refaktorovat Microsoft C Runtime Library (CRT). Standardní knihovny jazyka C, rozšíření POSIX a specifické pro společnost Microsoft funkcích, makra a globální proměnné se přesunuly do nové knihovny univerzální běhové knihovny jazyka C (Universal CRT nebo UCRT). Specifické pro kompilátor součástí CRT byly přesunuty do nové knihovny vcruntime.  
  
UCRT je teď součástí Windows a dodává v rámci Windows 10. UCRT podporuje stabilní ABI podle konvence volání jazyka C a vyhovuje úzce standard s pouze několika výjimkami ISO C99. Již je spojený s specifické verzi kompilátoru. Můžete použít UCRT na libovolnou verzi systému Windows podporuje Visual Studio 2015 nebo Visual Studio 2017. Výhodou je, že už nemusíte aktualizovat buildy a cílit na novou verzi CRT při každém upgradu sady Visual Studio.  
  
Tento refaktorování, změnily se názvy nebo umístění mnoho CRT hlavičkové soubory, soubory knihovny a distribuovatelné součásti a metody nasazení pro váš kód vyžaduje. Kromě toho mnoha funkcemi a makry v UCRT přidané nebo změnit ke zlepšení shoda se standardy. Abyste mohli využívat tyto změny, se musí aktualizovat váš stávající kód a systémy sestavení projektu.  
  
## <a name="where-to-find-the-universal-crt-files"></a>Kde se mají hledat soubory Universal CRT

Jako Windows jsou teď součástí sady Windows software development kit (SDK) komponenty, UCRT soubory knihovny a hlavičky. Při instalaci sady Visual Studio, nainstaluje se také součástí Windows SDK, aby jeho používání UCRT. Instalační program sady Visual Studio přidá umístění UCRT hlavičky, knihovny a soubory DLL přidala k výchozím cestám používané projektu sady Visual Studio sestavovací systém. Při aktualizaci vašich projektů Visual C++, pokud používají výchozí nastavení projektu, rozhraní IDE automaticky vyhledá nové umístění pro soubory hlaviček a propojovací program automaticky použije nový výchozí UCRT a vcruntime knihovny. Podobně pokud pomocí příkazového řádku pro vývojáře provádět sestavení příkazového řádku, prostředí, ve kterém proměnné, které obsahují cesty pro hlavičky a knihovny se aktualizují a automaticky i práce.  
  
Souborech hlaviček standardní knihovny jazyka C jsou teď součástí sady Windows SDK v zahrnout složku v adresáři konkrétní verze sady SDK. Obvyklé umístění pro soubory hlaviček je ve složce Program Files nebo Program Files (x86) adresář v rámci sady Windows\\10\\zahrnout\\_verze sady sdk_\\ucrt, kde _verze sady sdk_ odpovídá verzi Windows nebo aktualizace, například 10.0.14393.0 Anniversary Update sady Windows 10.   
  
UCRT statických knihoven a knihovny DLL zástupných procedur se nacházejí ve složce Program Files nebo Program Files (x86) adresář v rámci sady Windows\\10\\Lib\\_verze sady sdk_\\ucrt \\ _architektura_, kde _architektura_ je ARM, x 86 nebo X64. Statické knihovny maloobchodních a ladicích jsou libucrt.lib a libucrtd.lib a knihovny pro knihovny DLL UCRT jsou ucrt.lib a ucrtd.lib.  
  
Maloobchodní prodej a ladění knihoven DLL UCRT se nacházejí v různých umístěních. Maloobchodní knihovny DLL jsou šiřitelné a najdete ve složce Program Files nebo Program Files (x86) adresář v rámci sady Windows\\10\\Redist\\ucrt\\knihovny DLL\\_architektury_\. Ladění UCRT nejsou opakovaně distribuovatelné knihovny a najdete ve složce Program Files nebo Program Files (x86) adresář v rámci sady Windows\\10\\bin\\_architektura_\\ucrt složka.   

C a C++ specifických pro kompilátor podporu knihovně runtime **vcruntime**, obsahuje kód potřebné k podpoře spuštění programu a funkce jako je zpracování výjimek a vnitřní funkce. Knihovny a soubory hlaviček se stále nacházejí ve složce specifické pro verzi sady Microsoft Visual Studio v adresáři Program files (x86) nebo Program Files. V sadě Visual Studio 2017, se nacházejí záhlaví v rámci sady Microsoft Visual Studio\\2017\\_edition_\\VC\\nástroje\\MSVC\\  _lib – verze_\\zahrnout a jsou v ní odkaz knihovny v rámci sady Microsoft Visual Studio\\2017\\_edition_\\VC\\nástroje \\MSVC\\_lib verze_\\lib\\_architektura_, kde _edition_ je vydání sady Visual Studio nainstalovaný _lib verze_ je verze knihoven, a _architektura_ je na architektuře procesoru. Odkaz knihovny pro OneCore a Store se taky nacházejí ve složce knihovny. Verze maloobchodních a ladicích statické knihovny jsou libvcruntime.lib a libvcruntimed.lib. Knihovny DLL maloobchodních a ladicích zástupné procedury jsou vcruntime.lib a vcruntimed.lib.  
  
Při aktualizaci vašich projektů Visual C++, pokud jste nastavili v projektu **Linkeru** vlastnost **ignorovat všechny výchozí knihovny** k **Ano** nebo pokud používáte `/NODEFAULTLIB` na příkazovém řádku a potom – možnost linkeru musíte aktualizovat seznam knihovny k začlenění refaktorované, nové knihovny. Nahraďte původní knihovny CRT, například libcmt.lib, libcmtd.lib, msvcrt.lib nebo msvcrtd.lib, ekvivalentní refaktorovaný knihovny. Informace o konkrétní knihovny používat, naleznete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).  
  
## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Nasazení a distribuci na Universal CRT
  
Vzhledem k tomu, UCRT je teď součástí operačního systému Microsoft Windows, je součástí operačního systému ve Windows 10 a je dostupná prostřednictvím služby Windows Update pro starší operační systémy Windows Vista až Windows 8.1. Redistributable verze je k dispozici pro Windows XP. Jako součást operačního systému se službou Windows Update spravují UCRT aktualizace a údržba, bez ohledu na jejich verze kompilátoru Visual Studio a Microsoft C++. Vzhledem k tomu, UCRT je komponenta Windows pro zabezpečení a snadné aktualizací a menší velikost obrázku, důrazně doporučujeme centrální nasazení UCRT pro vaši aplikaci.  
  
Můžete použít UCRT na libovolnou verzi systému Windows podporuje Visual Studio 2015 nebo Visual Studio 2017. Můžete znovu distribuovat pomocí balíčku pro balíček vcredist pro podporované verze systému Windows než Windows 10. Balíčky vcredist UCRT komponenty a automaticky nainstalují operačních systémech Windows, které nemají je ve výchozím nastavení nainstalovaná. Další informace najdete v tématu [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
Aplikace – místní nasazení UCRT se podporuje, ale nedoporučuje se z důvodů výkonu a zabezpečení. Knihovny DLL pro nasazení místní aplikace jsou zahrnuté jako součást sady Windows SDK, v části **redist** podadresáře. Požadované knihovny DLL obsahovat ucrtbase.dll a sadu **APISet předávání** knihovny DLL s názvem rozhraní api-ms-win -_dílčí_.dll. Sadu knihoven DLL vyžaduje na všech operačních systémech liší, proto je vhodné zahrnout všechny knihovny DLL při použití aplikace místní nasazení. Upozornění o nasazení aplikace místní a další podrobnosti najdete v tématu [nasazení v jazyce Visual C++](../ide/deployment-in-visual-cpp.md).  
  
## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Změny na Universal CRT funkcemi a makry  

Mnoho funkcí přidaná nebo aktualizovaná UCRT ke zlepšení ISO C99 shoda a řešit problémy zabezpečení a kvalitní kód. V některých případech to vyžaduje rozbíjející změny v knihovně. Pokud váš kód zkompilován čistě používáte starší verzi CRT ale konce při kompilaci pomocí UCRT, je nutné změnit váš kód výhod těchto aktualizací a funkcí. Podrobné informace o nejnovější změny a aktualizace CRT v Universal CRT, najdete v článku [knihovny Runtime jazyka C (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) historii změn části Visual C++. Obsahuje seznam ovlivněných záhlaví a funkce, které vám umožní identifikovat změny potřebné v kódu.  
  
## <a name="see-also"></a>Viz také  

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)  
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)  
[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)  