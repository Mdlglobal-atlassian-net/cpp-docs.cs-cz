---
title: Upgrade kódu na Universal CRT
ms.date: 03/31/2017
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
ms.openlocfilehash: 0554ff713b499f99e7e7508faf687c1635e6d912
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627177"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Upgrade kódu na Universal CRT

V aplikaci Visual Studio 2015 byla refaktorovaná Knihovna CRT (Microsoft C Runtime Library). Standardní knihovna C, rozšíření POSIX a funkce specifické pro společnost Microsoft, makra a globální proměnné byly přesunuty do nové knihovny, knihovny Universal C Runtime Library (Universal CRT nebo UCRT). Komponenty CRT specifické pro kompilátor byly přesunuty do nové knihovny vcruntime.

UCRT je teď součástí Windows a dodává se jako součást Windows 10. UCRT podporuje stabilní ABI v závislosti na konvencích volání jazyka C a je v souladu se standardem ISO C99, a to pouze s několika výjimkami. Již není vázána na konkrétní verzi kompilátoru. UCRT můžete použít na všech verzích Windows, které podporuje Visual Studio 2015 nebo Visual Studio 2017. Výhodou je, že už nebudete muset aktualizovat vaše sestavení, aby bylo možné cílit na novou verzi CRT s každým upgradem sady Visual Studio.

Pomocí tohoto refaktoringu jsou názvy nebo umístění mnoha souborů hlaviček CRT, soubory knihoven a distribuovatelné a metody nasazení vyžadované pro váš kód se změnily. Kromě toho mnoho funkcí a maker v UCRT byly přidány nebo změněny pro zlepšení dodržování standardů. Chcete-li využít tyto změny, je nutné aktualizovat existující systémy kódu a sestavení projektů.

## <a name="where-to-find-the-universal-crt-files"></a>Kde najít soubory Universal CRT

Jako součást systému Windows jsou nyní soubory a hlavičky knihovny UCRT součástí sady Windows Software Development Kit (SDK). Při instalaci sady Visual Studio jsou nainstalovány také součásti Windows SDK nutné pro použití nástroje UCRT. Instalační program sady Visual Studio přidá umístění hlaviček UCRT, knihoven a souborů DLL do výchozích cest používaných systém sestavení projektu sady Visual Studio. Při aktualizaci projektů aplikace Visual Studio C++ , pokud používají výchozí nastavení projektu, rozhraní IDE automaticky najde nová umístění pro hlavičkové soubory a linker automaticky použije nové výchozí knihovny UCRT a vcruntime. Podobně platí, že pokud použijete příkazové okno pro vývojáře k provádění sestavení příkazového řádku, jsou proměnné prostředí obsahující cesty k hlavičkám a knihovnám aktualizovány a pracují také automaticky.

Standardní soubory hlaviček knihovny jazyka C se nyní nacházejí v Windows SDK ve složce include v adresáři určeném pro danou verzi sady SDK. Obvyklé umístění hlavičkových souborů je v adresáři Program Files nebo Program Files (x86) ve Windows Kits\\10\\zahrnují\\_SDK-version_\\UCRT, kde _verze sady SDK_ odpovídá verzi Windows nebo aktualizace, například 10.0.14393.0 pro výroční aktualizaci Windows 10.

Statické knihovny UCRT a knihovny zástupných procedur dynamického propojení se nacházejí v adresáři Program Files nebo Program Files (x86) v části sady Windows\\10\\lib\\_SDK-version_\\UCRT\\_Architecture_, kde  _Architektura_ je ARM, x86 nebo x64. Maloobchodní a ladicí statické knihovny jsou libucrt. lib a libucrtd. lib a knihovny pro knihovny DLL UCRT jsou UCRT. lib a ucrtd. lib.

Maloobchodní a ladicí UCRT knihovny DLL se nacházejí v různých umístěních. Maloobchodní knihovny DLL jsou distribuovatelné a dají se najít v adresáři Program Files nebo Program Files (x86) v části sady Windows\\10\\Redist\\UCRT\\DLL\\_architektuře_\. Ladění knihoven UCRT není Distribuovatelný a najdete je v adresáři Program Files nebo Program Files (x86) v části sady Windows\\10\\bin\\_architektury_\\složce UCRT.

Knihovna podpory modulu C++ runtime **vcruntime**specifická pro jazyk C a kompilátor obsahuje kód potřebný k podpoře spuštění programu a funkcí, jako je například zpracování výjimek a vnitřní objekty. Knihovna a její hlavičkové soubory se pořád nacházejí ve složce pro Microsoft Visual Studio pro konkrétní verzi v adresáři Program Files nebo Program Files (x86). V aplikaci Visual Studio 2017 se hlavičky nacházejí v části Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-Version_\\include a knihovny odkazů se nacházejí v rámci společnosti Microsoft. Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-version_\\lib\\_Architecture_, kde _Edition_ je edice sady Visual Studio nainstalováno, _lib-Version_ je verze knihoven a _Architektura_ je architekturou procesoru. Knihovny odkazů pro OneCore a Store se také nacházejí ve složce knihovny. Maloobchodní a ladicí verze statické knihovny jsou libvcruntime. lib a libvcruntimed. lib. Knihovny pro maloobchodního zástupné procedury pro dynamické propojení a ladění jsou vcruntime. lib a vcruntimed. lib v uvedeném pořadí.

Když aktualizujete projekty aplikace Visual C++ Studio, pokud jste nastavili vlastnost **linkeru** projektu **Ignorovat všechny výchozí knihovny** na **Ano** nebo pokud použijete možnost `/NODEFAULTLIB` linkeru na příkazovém řádku, je nutné aktualizovat seznam knihovny, které obsahují nové, refaktorované knihovny. Nahraďte starou knihovnu CRT, například Libcmt. lib, LIBCMTD. lib, Msvcrt. lib nebo msvcrtd. lib, se stejnými refaktoring knihovny. Informace o konkrétních knihovnách, které se mají použít, najdete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Nasazení a redistribuce univerzálního CRT

Vzhledem k tomu, že UCRT je teď součástí operačního systému Microsoft Windows, je součástí operačního systému Windows 10 a je k dispozici prostřednictvím web Windows Update pro starší operační systémy, Windows Vista prostřednictvím Windows 8.1. Pro systém Windows XP je k dispozici Redistribuovatelná verze. UCRT aktualizace a údržba jako součást operačního systému se spravují pomocí web Windows Update nezávisle na verzích Visual studia a C++ kompilátoru Microsoft. Vzhledem k tomu, že UCRT je součást systému Windows, z důvodu zabezpečení a snadné aktualizace a menší velikosti obrázku, důrazně doporučujeme centrální nasazení UCRT pro vaši aplikaci.

UCRT můžete použít na všech verzích Windows, které podporuje Visual Studio 2015 nebo Visual Studio 2017. Můžete ji znovu distribuovat pomocí balíčku VCRedist pro podporované verze Windows, které jsou jiné než Windows 10. Balíčky VCRedist zahrnují komponenty UCRT a automaticky je instalují do operačních systémů Windows, které je ve výchozím nastavení nenainstalovaly. Další informace najdete v tématu [Redistribuce vizuálních C++ souborů](../windows/redistributing-visual-cpp-files.md).

Místní nasazení UCRT pro aplikaci se podporuje, ale nedoporučuje se z důvodů výkonu i zabezpečení. Knihovny DLL pro nasazení v rámci aplikace jsou součástí Windows SDK v podadresáři **Redist** . Požadované knihovny DLL zahrnují ucrtbase. dll a sadu knihoven DLL **pro přeposílání APISet** s názvem API-MS-Win-_podmnožin_. dll. Sada knihoven DLL, které jsou nutné v každém operačním systému, se liší, takže při použití místního nasazení aplikace doporučujeme zahrnout všechny knihovny DLL. Další podrobnosti a upozornění týkající se nasazení v místním prostředí najdete v tématu [nasazení v vizuálu C++ ](../windows/deployment-in-visual-cpp.md).

## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Změny Universal CRT functions a maker

Do UCRT bylo přidáno nebo aktualizováno mnoho funkcí, které zlepšují dodržování standardu ISO C99 a řeší problémy s kvalitou a zabezpečením kódu. V některých případech to vyžaduje zásadní změny v knihovně. Pokud je váš kód zkompilován čistě při použití starší verze CRT, ale při kompilování pomocí UCRT, je nutné změnit kód a využít tyto aktualizace a funkce. Podrobný seznam konců změn a aktualizací CRT nalezeného v univerzálním CRT naleznete v části [Knihovna prostředí C runtime (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) v historii vizuálních C++ změn. Obsahuje seznam ovlivněných hlaviček a funkcí, které můžete použít k identifikaci změn potřebných ve vašem kódu.

## <a name="see-also"></a>Viz také:

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)<br/>
[Přehled potenciálních problémů s upgradem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Upgrade projektů z dřívějších verzí sady VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Historie změn Visual C++ 2003–2015](visual-cpp-change-history-2003-2015.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)
