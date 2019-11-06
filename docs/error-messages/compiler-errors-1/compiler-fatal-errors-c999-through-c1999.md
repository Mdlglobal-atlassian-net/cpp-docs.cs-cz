---
title: Závažné chyby kompilátoru C999 až C1999
ms.date: 04/21/2019
f1_keywords:
- C1034
- C1036
- C1041
- C1048
- C1063
- C1069
- C1101
- C1102
- C1105
- C1110
- C1111
- C1112
- C1114
- C1193
- C1195
- C1300
- C1301
- C1302
- C1306
- C1384
- C1451
- C1505
- C1901
helpviewer_keywords:
- C1034
- C1036
- C1041
- C1048
- C1063
- C1069
- C1101
- C1102
- C1105
- C1110
- C1111
- C1112
- C1114
- C1193
- C1195
- C1300
- C1301
- C1302
- C1306
- C1384
- C1451
- C1505
- C1901
ms.assetid: 6c8df109-7594-48ed-987a-97d9fe2b04af
ms.openlocfilehash: 395d7403ef4fe04b671a84a61d320b27ad8ad1c7
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626571"
---
# <a name="compiler-fatal-errors-c999-through-c1999"></a>Závažné chyby kompilátoru C999 až C1999

Články v této části dokumentace vysvětlují podmnožinu chybových zpráv, které jsou generovány společností Microsoft C/C++ Compiler.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Závažná chyba C999](../../error-messages/compiler-errors-1/fatal-error-c999.md)|NEZNÁMÁ zpráva Pokud chcete získat další informace, zvolte prosím příkaz C++ technická podpora v nabídce Visual Help, nebo otevřete soubor s podporou technické podpory.|
|[Závažná chyba C1001](../../error-messages/compiler-errors-1/fatal-error-c1001.md)|V kompilátoru došlo k vnitřní chybě.<br /> (soubor kompilátoru '*File*', *číslo*řádku)<br /> Pokud chcete tento problém obejít, zkuste zjednodušit nebo změnit program poblíž výše uvedených umístění. Pokud chcete získat další informace, zvolte prosím příkaz C++ technická podpora v nabídce Visual Help, nebo otevřete soubor s podporou technické podpory.|
|[Závažná chyba C1002](../../error-messages/compiler-errors-1/fatal-error-c1002.md)|Kompilátor má nedostatek prostoru v haldě v Pass 2.|
|[Závažná chyba C1003](../../error-messages/compiler-errors-1/fatal-error-c1003.md)|počet chyb překračuje *číslo*; zastavování kompilace|
|[Závažná chyba C1004](../../error-messages/compiler-errors-1/fatal-error-c1004.md)|našel se neočekávaný konec souboru.|
|[Závažná chyba C1005](../../error-messages/compiler-errors-1/fatal-error-c1005.md)|řetězec je pro vyrovnávací paměť moc velký.|
|[Závažná chyba C1007](../../error-messages/compiler-errors-1/fatal-error-c1007.md)|nerozpoznaný příznak "*String*" v "*Option*"|
|[Závažná chyba C1008](../../error-messages/compiler-errors-1/fatal-error-c1008.md)|nebyl zadán vstupní soubor.|
|[Závažná chyba C1009](../../error-messages/compiler-errors-1/fatal-error-c1009.md)|limit kompilátoru: makra jsou vnořená moc hluboko.|
|[Závažná chyba C1010](../../error-messages/compiler-errors-1/fatal-error-c1010.md)|při hledání předkompilované hlavičky byl zjištěn neočekávaný konec souboru. Nezapomněli jste do zdroje přidat *soubor*#include \<>?|
|[Závažná chyba C1012](fatal-error-c1012.md)|nespárovaná závorka: chybí*znak "Character*".|
|[Závažná chyba C1013](fatal-error-c1013.md)|limit kompilátoru: moc velký počet levých závorek.|
|[Závažná chyba C1014](fatal-error-c1014.md)|moc velký počet vložených souborů: Hloubka = *číslo*|
|[Závažná chyba C1016](fatal-error-c1016.md)|byl očekáván identifikátor #ifdef/#ifndef|
|[Závažná chyba C1017](../../error-messages/compiler-errors-1/fatal-error-c1017.md)|neplatný výraz konstanty typu Integer|
|[Závažná chyba C1018](fatal-error-c1018.md)|Neočekávaná #elif|
|[Závažná chyba C1019](fatal-error-c1019.md)|Neočekávaná #else|
|[Závažná chyba C1020](fatal-error-c1020.md)|Neočekávaná #endif|
|[Závažná chyba C1021](fatal-error-c1021.md)|Neplatný příkaz preprocesoru "*String*"|
|[Závažná chyba C1022](fatal-error-c1022.md)|očekávané #endif|
|[Závažná chyba C1023](fatal-error-c1023.md)|'*File*': došlo k neočekávané chybě souboru PCH, zkuste soubor PCH znovu sestavit.|
|[Závažná chyba C1026](../../error-messages/compiler-errors-1/fatal-error-c1026.md)|přetečení zásobníku analyzátoru, program je moc složitý.|
|[Závažná chyba C1033](../../error-messages/compiler-errors-1/fatal-error-c1033.md)|Nelze otevřít databázi programu '*File*'|
|Závažná chyba C1034|*soubor*: není nastavená cesta pro zahrnutí.|
|[Závažná chyba C1035](fatal-error-c1035.md)|výraz je moc složitý; zjednodušit výraz|
|Závažná chyba C1036|nelze přepsat dřívější formát databáze programu, odstranit*soubor*a znovu kompilovat|
|[Závažná chyba C1037](fatal-error-c1037.md)|nejde*otevřít soubor objektu.*|
|[Závažná chyba C1038](fatal-error-c1038.md)|limit kompilátoru:*Function*: stav toku ovládacích prvků je moc složitý; jednodušší funkce|
|Závažná chyba C1041|Nelze otevřít databázi programu '*File*'; Pokud je více CL. EXE zapisovat do stejného. Soubor PDB, použijte prosím/FS.|
|[Závažná chyba C1045](fatal-error-c1045.md)|limit kompilátoru: specifikace propojení jsou vnořené moc hluboko.|
|[Závažná chyba C1046](../../error-messages/compiler-errors-1/fatal-error-c1046.md)|limit kompilátoru: *Struktura* je vnořená moc hluboko.|
|[Závažná chyba C1047](fatal-error-c1047.md)|Soubor*nebo soubor knihovny*byl vytvořen pomocí staršího kompilátoru než jiné objekty. znovu sestavit staré objekty a knihovny|
|Závažná chyba C1048|Neznámá možnost '*String*' v '*Option*'|
|[Závažná chyba C1049](fatal-error-c1049.md)|Neplatný číselný argument*Value*|
|[Závažná chyba C1051](../../error-messages/compiler-errors-1/fatal-error-c1051.md)|soubor databáze programu,*soubor*, má zastaralý formát, odstraňte ho a znovu zkompilujte.|
|[Závažná chyba C1052](fatal-error-c1052.md)|soubor databáze programu, '*filename*', byl vygenerován linkerem s parametrem/Debug: FastLink; Kompilátor nemůže aktualizovat takové soubory PDB; odstraňte ho prosím nebo použijte/FD a zadejte jiný název souboru PDB.|
|[Závažná chyba C1053](fatal-error-c1053.md)|'*Function*': funkce je příliš velká|
|[Závažná chyba C1054](../../error-messages/compiler-errors-1/fatal-error-c1054.md)|limit kompilátoru: Inicializátory jsou vnořené moc hluboko.|
|[Závažná chyba C1055](../../error-messages/compiler-errors-1/fatal-error-c1055.md)|limit kompilátoru: došly klíče.|
|[Závažná chyba C1057](../../error-messages/compiler-errors-1/fatal-error-c1057.md)|Neočekávaný konec souboru v rozšíření makra|
|[Závažná chyba C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)|Kompilátor má nedostatek prostoru v haldě.|
|[Závažná chyba C1061](../../error-messages/compiler-errors-1/fatal-error-c1061.md)|limit kompilátoru: bloky jsou vnořené moc hluboko.|
|Závažná chyba C1063|limit kompilátoru: přetečení zásobníku kompilátoru|
|[Závažná chyba C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)|limit kompilátoru: token způsobil přetečení vnitřní vyrovnávací paměti.|
|[Závažná chyba C1065](../../error-messages/compiler-errors-1/fatal-error-c1065.md)|limit kompilátoru: došly značky.|
|[Závažná chyba C1067](../../error-messages/compiler-errors-1/fatal-error-c1067.md)|limit kompilátoru: překročil se limit 64 KB pro velikost záznamu typu.|
|[Závažná chyba C1068](fatal-error-c1068.md)|soubor '*File*' nelze otevřít.|
|Závažná chyba C1069|nejde přečíst příkazový řádek kompilátoru.|
|[Závažná chyba C1070](fatal-error-c1070.md)|neodpovídající dvojice #if/#endif v souboru '*File*'|
|[Závažná chyba C1071](../../error-messages/compiler-errors-1/fatal-error-c1071.md)|v komentáři se našel neočekávaný konec souboru.|
|[Závažná chyba C1073](../../error-messages/compiler-errors-1/fatal-error-c1073.md)|Vnitřní chyba týkající se přírůstkové kompilace (soubor kompilátoru '*File*', *číslo*řádku)|
|[Závažná chyba C1074](fatal-error-c1074.md)|' IDB ' je neplatný přípona *souboru PDB:*|
|[Závažná chyba C1075](../../error-messages/compiler-errors-1/fatal-error-c1075.md)|levý *token* se neshodoval na konci souboru.|
|[Závažná chyba C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)|limit kompilátoru: dosažen vnitřní limit haldy; použití/zm k určení vyššího limitu|
|[Závažná chyba C1077](fatal-error-c1077.md)|limit kompilátoru: nemůže mít víc než tento *počet* parametrů příkazového řádku:|
|[Závažná chyba C1079](../../error-messages/compiler-errors-1/fatal-error-c1079.md)|limit kompilátoru: překročil se limit velikosti souboru PCH.|
|[Závažná chyba C1080](../../error-messages/compiler-errors-1/fatal-error-c1080.md)|limit kompilátoru: parametr příkazového řádku překročil limit *počtu* znaků.|
|[Závažná chyba C1081](../../error-messages/compiler-errors-1/fatal-error-c1081.md)|'*File*': název souboru je příliš dlouhý.|
|[Závažná chyba C1082](fatal-error-c1082.md)|nelze zavřít *typ* souboru:*soubor*: *zpráva*|
|[Závažná chyba C1083](../../error-messages/compiler-errors-1/fatal-error-c1083.md)|nejde otevřít soubor s *typem* :*File*: *Message* .|
|[Závažná chyba C1084](../../error-messages/compiler-errors-1/fatal-error-c1084.md)|Nelze číst soubor *typu* :*soubor*: *zpráva*|
|[Závažná chyba C1085](../../error-messages/compiler-errors-1/fatal-error-c1085.md)|nejde zapisovat do souboru *typu* :*File*: *Message* .|
|[Závažná chyba C1086](fatal-error-c1086.md)|Nelze vyhledat soubor *typu* : '*File*': *Message*|
|[Závažná chyba C1087](fatal-error-c1087.md)|nelze sdělit *typ* souboru: '*File*': *Message*|
|[Závažná chyba C1088](fatal-error-c1088.md)|nejde vyprázdnit soubor *typu* :*soubor*: *zpráva*|
|[Závažná chyba C1089](fatal-error-c1089.md)|nejde zkrátit soubor *typu* :*soubor*: *zpráva*|
|Závažná chyba C1090|Volání rozhraní PDB API selhalo, kód chyby:*kód*:*zpráva*|
|[Závažná chyba C1091](fatal-error-c1091.md)|limit kompilátoru: řetězec překračuje délku *počtu* bajtů.|
|[Závažná chyba C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)|Upravit a pokračovat nepodporuje změny datových typů; požadováno sestavení|
|[Závažná chyba C1093](../../error-messages/compiler-errors-1/fatal-error-c1093.md)|Volání rozhraní API '*Function*' selhalo '*HRESULT*': '*Description*'|
|[Závažná chyba C1094](../../error-messages/compiler-errors-1/fatal-error-c1094.md)|-Zm*číslo*: možnost příkazového řádku není konzistentní s hodnotou použitou k sestavení předkompilované hlavičky (-zm*Number*).|
|[Závažná chyba C1098](fatal-error-c1098.md)|Neshoda verzí s modulem upravit a pokračovat|
|[Závažná chyba C1099](fatal-error-c1099.md)|Ukončovací kompilace modulu upravit a pokračovat|
|[Závažná chyba C1100](fatal-error-c1100.md)|Nelze inicializovat OLE: *Chyba*|
|Závažná chyba C1101|Nejde vytvořit obslužnou rutinu pro atribut*Identifier*.|
|Závažná chyba C1102|nelze provést inicializaci: *Chyba*|
|[Závažná chyba C1103](fatal-error-c1103.md)|Závažná chyba při importu ProgID: '*Message*'|
|[Závažná chyba C1104](fatal-error-c1104.md)|Závažná chyba při importu LIBID: '*Message*'|
|Závažná chyba C1105|*zpráva*: *Chyba*|
|[Závažná chyba C1107](../../error-messages/compiler-errors-1/fatal-error-c1107.md)|Nepovedlo se najít*sestavení Assembly:* zadejte prosím cestu pro vyhledávání sestavení pomocí/AI nebo nastavte PROMĚNNOU prostředí LIBPATH.|
|[Závažná chyba C1108](fatal-error-c1108.md)|Nepovedlo se najít DLL:*File*.|
|[Závažná chyba C1109](fatal-error-c1109.md)|v*souboru*dll se nepovedlo najít*symbol*.|
|Závažná chyba C1110|moc velký počet vnořených šablon/obecných definic|
|Závažná chyba C1111|moc velký počet šablon/obecných parametrů|
|Závažná chyba C1112|limit kompilátoru: `'number`moc velký počet argumentů makra, je povolené jenom *číslo* .|
|[Závažná chyba C1113](../../error-messages/compiler-errors-1/fatal-error-c1113.md)|Nepovedlo se #using*soubor*|
|Závažná chyba C1114|'*File*': WinRT nepodporuje #using spravovaného sestavení.|
|[Závažná chyba C1120](../../error-messages/compiler-errors-1/fatal-error-c1120.md)|volání GetProcAddress selhalo pro*Function*.|
|[Závažná chyba C1121](../../error-messages/compiler-errors-1/fatal-error-c1121.md)|volání CryptoAPI selhalo.|
|[Závažná chyba C1126](../../error-messages/compiler-errors-1/fatal-error-c1126.md)|automatické přidělování překračuje *Velikost*|
|[Závažná chyba C1128](../../error-messages/compiler-errors-1/fatal-error-c1128.md)|počet oddílů překročil limit formátu souboru objektů: kompilovat pomocí/bigobj|
|[Závažná chyba C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)|#error: *zpráva*|
|[Závažná chyba C1190](fatal-error-c1190.md)|spravovaný cílový kód vyžaduje možnost/CLR.|
|[Závažná chyba C1191](../../error-messages/compiler-errors-1/fatal-error-c1191.md)|*soubor*se dá importovat jedině v globálním oboru.|
|[Závažná chyba C1192](../../error-messages/compiler-errors-1/fatal-error-c1192.md)|Nepovedlo se #using*soubor*|
|Závažná chyba C1193|v *souboru*(*řádku*) se nedostala chyba.|
|Závažná chyba C1195|použití/Yu a/YC na stejném příkazovém řádku není kompatibilní s možností/CLR.|
|[Závažná chyba C1196](fatal-error-c1196.md)|'*Identifier*': identifikátor nalezen v knihovně typů '*TypeLib*' není platný C++ identifikátor|
|[Závažná chyba C1197](../../error-messages/compiler-errors-1/fatal-error-c1197.md)|nejde odkazovat na*soubor*, protože program už odkazoval na*soubor*.|
|[Závažná chyba C1201](fatal-error-c1201.md)|nejde pokračovat po chybě syntaxe v definici šablony třídy.|
|[Závažná chyba C1202](fatal-error-c1202.md)|Rekurzivní typ nebo kontext závislosti funkce je moc složitý.|
|[Závažná chyba C1205](fatal-error-c1205.md)|Obecné typy nejsou nainstalovanou verzí modulu runtime podporované.|
|[Závažná chyba C1206](fatal-error-c1206.md)|Data pro každou doménu AppDomain nejsou podporovaná ve verzi nainstalovaného modulu runtime.|
|[Závažná chyba C1207](fatal-error-c1207.md)|Spravované šablony nejsou podporované nainstalovanou verzí modulu runtime.|
|[Závažná chyba C1208](fatal-error-c1208.md)|Přidělení referenčních tříd v zásobníku není podporované nainstalovanou verzí modulu runtime.|
|[Závažná chyba C1209](fatal-error-c1209.md)|Sestavení Friend nejsou podporovaná nainstalovanou verzí modulu runtime.|
|[Závažná chyba C1210](fatal-error-c1210.md)|/CLR: Pure a/CLR: safe nejsou podporované nainstalovanou verzí modulu runtime.|
|[Závažná chyba C1211](fatal-error-c1211.md)|Vlastní atribut TypeForwardedTo není podporován nainstalovanou verzí modulu runtime.|
|Závažná chyba C1300|Chyba při přístupu k *souboru* databáze programu (*zpráva*)|
|Závažná chyba C1301|Chyba při přístupu k *souboru*databáze programu, neplatný formát, prosím odstraňte a znovu sestavte.|
|Závažná chyba C1302|žádná data profilu pro modul*Module*v databázi profilu '*File*'|
|[Závažná chyba C1305](../../error-messages/compiler-errors-1/fatal-error-c1305.md)|profilová databáze '*soubor*' je pro jinou architekturu|
|Závažná chyba C1306|Poslední změna základu dat profilu '*File*' nebyla analýzou optimalizace; rozhodnutí o optimalizaci můžou být zastaralá.|
|[Závažná chyba C1307](../../error-messages/compiler-errors-1/fatal-error-c1307.md)|program se od shromáždění dat profilu upravoval.|
|[Závažná chyba C1308](../../error-messages/compiler-errors-1/fatal-error-c1308.md)|*soubor*: propojení sestavení není podporováno.|
|[Závažná chyba C1309](../../error-messages/compiler-errors-1/fatal-error-c1309.md)|Neshodné verze C2. DLL a PGODB*ver*. DLL|
|[Závažná chyba C1310](fatal-error-c1310.md)|optimalizace na základě profilu nejsou s OpenMP k dispozici.|
|[Závažná chyba C1311](../../error-messages/compiler-errors-1/fatal-error-c1311.md)|Formát COFF nemůže staticky inicializovat*symbol*s *počtem* bajtů adresy.|
|[Závažná chyba C1312](fatal-error-c1312.md)|Funkce má příliš mnoho podmíněných větví.  Zjednodušte nebo refaktorujte zdrojový kód.|
|[Závažná chyba C1313](../../error-messages/compiler-errors-1/fatal-error-c1313.md)|limit kompilátoru: bloky *typů* nemůžou být vnořené hlouběji než úrovně *čísel* .|
|[Závažná chyba C1350](../../error-messages/compiler-errors-1/fatal-error-c1350.md)|Při načítání*souboru*dll došlo k chybě: knihovna DLL nebyla nalezena.|
|[Závažná chyba C1351](../../error-messages/compiler-errors-1/fatal-error-c1351.md)|Chyba při načítání*souboru*dll: nekompatibilní verze|
|[Závažná chyba C1352](fatal-error-c1352.md)|Neplatný nebo poškozený jazyk MSIL ve funkci*Function*z modulu*Module*|
|[Závažná chyba C1353](fatal-error-c1353.md)|operace metadat selhala: modul runtime není nainstalovaný nebo se neshoduje s verzí.|
|[Závažná chyba C1382](../../error-messages/compiler-errors-1/fatal-error-c1382.md)|soubor PCH "*File*" byl znovu vytvořen, protože objekt*obj*byl vygenerován. Sestavte prosím tento objekt znovu.|
|[Závažná chyba C1383](fatal-error-c1383.md)|možnost kompilátoru/GL není kompatibilní s nainstalovanou verzí modulu CLR (Common Language Runtime).|
|Závažná chyba C1384|Nesprávné nastavení pro PGO_PATH_TRANSLATION při propojování*souboru*|
|Závažná chyba C1451|Nepodařilo se vygenerovat informace o ladění při kompilování grafu volání pro: concurrency::p arallel_for_each v: '*CallSite.* '.|
|Závažná chyba C1505|Neopravitelná chyba analyzátoru při vyhledávání|
|[Závažná chyba C1506](../../error-messages/compiler-errors-1/fatal-error-c1506.md)|Neopravitelná chyba při vytváření oboru bloku|
|[Závažná chyba C1508](fatal-error-c1508.md)|limit kompilátoru:*Function*: víc než 65535 bajtů argumentu|
|[Závažná chyba C1509](../../error-messages/compiler-errors-1/fatal-error-c1509.md)|limit kompilátoru: ve funkci*Function Function*je moc velký počet stavů obslužných rutin výjimek. jednodušší funkce|
|[Závažná chyba C1510](../../error-messages/compiler-errors-1/fatal-error-c1510.md)|Nejde otevřít jazykový prostředek clui. dll.|
|[Závažná chyba C1601](../../error-messages/compiler-errors-1/fatal-error-c1601.md)|nepodporované opcode vloženého sestavení|
|[Závažná chyba C1602](../../error-messages/compiler-errors-1/fatal-error-c1602.md)|Nepodporovaný vnitřní|
|[Závažná chyba C1603](../../error-messages/compiler-errors-1/fatal-error-c1603.md)|cíl větve vloženého sestavení je mimo rozsah podle *počtu* bajtů.|
|[Závažná chyba C1852](fatal-error-c1852.md)|'*File*' není platný soubor předkompilované hlavičky|
|[Závažná chyba C1853](../../error-messages/compiler-errors-1/fatal-error-c1853.md)|soubor předkompilovaného hlavičkového*souboru je*z předchozí verze kompilátoru, nebo je C++ Předkompilovaná hlavička a Vy ji používáte z C (nebo naopak).|
|[Závažná chyba C1854](../../error-messages/compiler-errors-1/fatal-error-c1854.md)|nelze přepsat informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: '*File*'|
|[Závažná chyba C1900](../../error-messages/compiler-errors-1/fatal-error-c1900.md)|Il – neshoda*mezi "Version*"*Number*"a"*Tool*"Version"*Number*"|
|Závažná chyba C1901|Vnitřní chyba správy paměti|
|[Závažná chyba C1902](../../error-messages/compiler-errors-1/fatal-error-c1902.md)|Neshoda správce databáze programu; Zkontrolujte prosím instalaci.|
|[Závažná chyba C1903](fatal-error-c1903.md)|Nepovedlo se provést obnovení z předchozích chyb. zastavování kompilace|
|[Závažná chyba C1904](fatal-error-c1904.md)|nesprávná interakce zprostředkovatele: '*File*'|
|[Závažná chyba C1905](../../error-messages/compiler-errors-1/fatal-error-c1905.md)|Front-end a back-end nejsou kompatibilní (musí cílit na stejný procesor).|

## <a name="see-also"></a>Viz také:

[Chyby aC++ upozornění pro nástroje C/kompilátor a sestavení](../compiler-errors-1/c-cpp-build-errors.md)
