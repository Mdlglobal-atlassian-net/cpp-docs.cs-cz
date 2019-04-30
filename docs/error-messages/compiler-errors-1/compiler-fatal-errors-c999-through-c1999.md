---
title: Závažné chyby kompilátoru C999 až C1999
ms.date: 04/21/2019
f1_keywords:
- C1034
- C1036
- C1041
- C1048
- C1049
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
- C1049
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
ms.openlocfilehash: 5ffa1a2633877c8a16eb424f1ddc100bfd6142b8
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344843"
---
# <a name="compiler-fatal-errors-c999-through-c1999"></a>Závažné chyby kompilátoru C999 až C1999

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány nástrojem Microsoft C /C++ kompilátoru.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Závažná chyba C999](../../error-messages/compiler-errors-1/fatal-error-c999.md)|Neznámá zpráva Zvolte prosím příkaz technická podpora v nabídce Nápověda pro Visual C++, nebo otevřete soubor nápovědy technické podpory pro další informace|
|[Závažná chyba C1001](../../error-messages/compiler-errors-1/fatal-error-c1001.md)|V kompilátoru došlo k vnitřní chybě.<br /> (soubor kompilátoru "*souboru*!, řádek *číslo*)<br /> Chcete-li tento problém vyřešit, zkuste zjednodušit nebo změnit program v blízkosti míst uvedených výše. Zvolte prosím příkaz technická podpora v nabídce Nápověda pro Visual C++, nebo otevřete soubor nápovědy technické podpory pro další informace|
|[Závažná chyba C1002](../../error-messages/compiler-errors-1/fatal-error-c1002.md)|kompilátoru je nedostatek místa v haldě při průchodu 2|
|[Závažná chyba C1003](../../error-messages/compiler-errors-1/fatal-error-c1003.md)|Počet chyb překračuje *číslo*; kompilace se zastavuje|
|[Závažná chyba C1004](../../error-messages/compiler-errors-1/fatal-error-c1004.md)|neočekávané ukončení souboru nalezen|
|[Závažná chyba C1005](../../error-messages/compiler-errors-1/fatal-error-c1005.md)|řetězec je moc velký pro vyrovnávací paměť|
|[Závažná chyba C1007](../../error-messages/compiler-errors-1/fatal-error-c1007.md)|nerozpoznaný příznak "*řetězec*"in"*možnost*.|
|[Závažná chyba C1008](../../error-messages/compiler-errors-1/fatal-error-c1008.md)|zadané žádné vstupní soubory|
|[Závažná chyba C1009](../../error-messages/compiler-errors-1/fatal-error-c1009.md)|limit kompilátoru: makra jsou vnořená moc hluboko|
|[Závažná chyba C1010](../../error-messages/compiler-errors-1/fatal-error-c1010.md)|Neočekávaný konec souboru při hledání předkompilované hlavičky. Nezapomněli jste přidat ' #include \< *souboru*> "ke zdroji?|
|[Závažná chyba C1012](fatal-error-c1012.md)|Neshoda závorek: chybí "*znak*"|
|[Závažná chyba C1013](fatal-error-c1013.md)|limit kompilátoru: moc velký počet levých závorek|
|[Závažná chyba C1014](fatal-error-c1014.md)|moc velký počet vložených souborů: hloubka = *číslo*|
|[Závažná chyba C1016](fatal-error-c1016.md)|ifndef #ifdef / # byl očekáván identifikátor|
|[Závažná chyba C1017](../../error-messages/compiler-errors-1/fatal-error-c1017.md)|Neplatný celočíselný konstantní výraz|
|[Závažná chyba C1018](fatal-error-c1018.md)|neočekávané #elif|
|[Závažná chyba C1019](fatal-error-c1019.md)|neočekávané #else|
|[Závažná chyba C1020](fatal-error-c1020.md)|neočekávané #endif|
|[Závažná chyba C1021](fatal-error-c1021.md)|Neplatný příkaz preprocesoru "*řetězec*.|
|[Závažná chyba C1022](fatal-error-c1022.md)|očekávané #endif|
|[Závažná chyba C1023](fatal-error-c1023.md)|"*souboru*': došlo k neočekávané chybě se zkuste znovu sestavit soubor pch|
|[Závažná chyba C1026](../../error-messages/compiler-errors-1/fatal-error-c1026.md)|přetečení zásobníku analyzátoru. program je moc složitý|
|[Závažná chyba C1033](../../error-messages/compiler-errors-1/fatal-error-c1033.md)|nejde otevřít databázi programu "*souboru*.|
|Závažná chyba C1034|*soubor*: žádné nenastavená cesta pro vložené|
|[Závažná chyba C1035](fatal-error-c1035.md)|výraz je příliš složitý; zjednodušit výraz|
|Závažná chyba C1036|nejde přepsat dřívější formát databáze programu, odstraňte "*souboru*" a překompilujte.|
|[Závažná chyba C1037](fatal-error-c1037.md)|nejde otevřít souboru objektu "*souboru*.|
|[Závažná chyba C1038](fatal-error-c1038.md)|limit kompilátoru: "*funkce*': ovládací prvek stavu toku moc složitý; Zjednodušte funkci|
|Závažná chyba C1041|nejde otevřít databázi programu "*souboru*"; Pokud více CL. Soubor EXE zapisovat do stejné. Soubor PDB souboru, použijte prosím /FS|
|[Závažná chyba C1045](fatal-error-c1045.md)|limit kompilátoru: Specifikace propojení jsou vnořené moc hluboko|
|[Závažná chyba C1046](../../error-messages/compiler-errors-1/fatal-error-c1046.md)|limit kompilátoru: *struktura* jsou vnořené moc hluboko|
|[Závažná chyba C1047](fatal-error-c1047.md)|Soubor objektu nebo knihovny '*souboru*' byl vytvořen pomocí staršího kompilátoru než jiné objekty; znovu sestavit starší objekty a knihovny|
|Závažná chyba C1048|Neznámý parametr '*řetězec*"in"*možnost*.|
|Závažná chyba C1049|Neplatný číselný argument '*hodnota*.|
|[Závažná chyba C1051](../../error-messages/compiler-errors-1/fatal-error-c1051.md)|soubor databáze programu "*souboru*', má zastaralý formát, odstraňte ho a překompilujte|
|[Závažná chyba C1052](fatal-error-c1052.md)|soubor databáze programu "*filename*', byl vygenerován linkerem s/Debug: fastlink; kompilátor nemůže takovéto soubory PDB aktualizovat, odstraňte jej nebo použijte parametr /Fd a zadejte jiný název souboru PDB|
|[Závažná chyba C1053](fatal-error-c1053.md)|"*funkce*': funkce je příliš velká|
|[Závažná chyba C1054](../../error-messages/compiler-errors-1/fatal-error-c1054.md)|limit kompilátoru: Inicializátory jsou vnořené moc hluboko|
|[Závažná chyba C1055](../../error-messages/compiler-errors-1/fatal-error-c1055.md)|limit kompilátoru: došly klíče|
|[Závažná chyba C1057](../../error-messages/compiler-errors-1/fatal-error-c1057.md)|Neočekávaný konec souboru začal v rozšíření makra|
|[Závažná chyba C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)|kompilátoru je nedostatek místa v haldě|
|[Závažná chyba C1061](../../error-messages/compiler-errors-1/fatal-error-c1061.md)|limit kompilátoru: bloky jsou vnořené moc hluboko|
|Závažná chyba C1063|limit kompilátoru: přetečení zásobníku kompilátoru|
|[Závažná chyba C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)|limit kompilátoru: token způsobil přetečení vnitřní vyrovnávací paměť|
|[Závažná chyba C1065](../../error-messages/compiler-errors-1/fatal-error-c1065.md)|limit kompilátoru: došly značky|
|[Závažná chyba C1067](../../error-messages/compiler-errors-1/fatal-error-c1067.md)|limit kompilátoru: Došlo k překročení 64 kB omezení velikosti záznamu typu|
|[Závažná chyba C1068](fatal-error-c1068.md)|Nelze otevřít soubor "*souboru*.|
|Závažná chyba C1069|nejde číst příkazový řádek kompilátoru|
|[Závažná chyba C1070](fatal-error-c1070.md)|Neshoda #if / #endif spárovat v souboru '*souboru*.|
|[Závažná chyba C1071](../../error-messages/compiler-errors-1/fatal-error-c1071.md)|Neočekávaný konec souboru v komentáři se našel|
|[Závažná chyba C1073](../../error-messages/compiler-errors-1/fatal-error-c1073.md)|Došlo k vnitřní chybě týkající se přírůstkové kompilace (soubor kompilátoru "*souboru*!, řádek *číslo*)|
|[Závažná chyba C1074](fatal-error-c1074.md)|"IDB" není platná přípona souboru PDB: *souboru*|
|[Závažná chyba C1075](../../error-messages/compiler-errors-1/fatal-error-c1075.md)|levé straně *token* byl bezkonkurenční na konci souboru|
|[Závažná chyba C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)|limit kompilátoru: dosažen; vnitřní limit haldy pomocí parametru /Zm nastavte vyšší limit|
|[Závažná chyba C1077](fatal-error-c1077.md)|limit kompilátoru: nelze mít více než *číslo* možnosti příkazového řádku|
|[Závažná chyba C1079](../../error-messages/compiler-errors-1/fatal-error-c1079.md)|limit kompilátoru: Překročen limit velikosti souboru PCH|
|[Závažná chyba C1080](../../error-messages/compiler-errors-1/fatal-error-c1080.md)|limit kompilátoru: příkazového řádku možnost překročil limit *číslo* znaků|
|[Závažná chyba C1081](../../error-messages/compiler-errors-1/fatal-error-c1081.md)|"*souboru*': název souboru je příliš dlouhý|
|[Závažná chyba C1082](fatal-error-c1082.md)|nelze zavřít *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1083](../../error-messages/compiler-errors-1/fatal-error-c1083.md)|Nelze otevřít *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1084](../../error-messages/compiler-errors-1/fatal-error-c1084.md)|Nelze číst *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1085](../../error-messages/compiler-errors-1/fatal-error-c1085.md)|Nelze zapsat *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1086](fatal-error-c1086.md)|Nelze vyhledat *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1087](fatal-error-c1087.md)|nejde provést operace tell *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1088](fatal-error-c1088.md)|nejde vyprázdnit *typ* souboru: "*souboru*': *zprávy*|
|[Závažná chyba C1089](fatal-error-c1089.md)|nejde zkrátit *typ* souboru: "*souboru*': *zprávy*|
|Závažná chyba C1090|Volání PDB API selhalo, kód chyby: '*kód*":"*zpráva*.|
|[Závažná chyba C1091](fatal-error-c1091.md)|limit kompilátoru: řetězec je delší než *číslo* délku bajtů|
|[Závažná chyba C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)|Upravit a pokračovat nepodporuje změny datových typů; požadované sestavení|
|[Závažná chyba C1093](../../error-messages/compiler-errors-1/fatal-error-c1093.md)|Volání rozhraní API "*funkce*'se nezdařil'*HRESULT*": "*popis*.|
|[Závažná chyba C1094](../../error-messages/compiler-errors-1/fatal-error-c1094.md)|"-Zm*číslo*': parametr příkazového řádku není konzistentní s hodnotou použitou k sestavení předkompilované hlavičky ("-Zm*číslo*")|
|[Závažná chyba C1098](fatal-error-c1098.md)|Neshoda verzí s modulem upravit a pokračovat|
|[Závažná chyba C1099](fatal-error-c1099.md)|Upravit a pokračovat ukončující kompilace modulu|
|[Závažná chyba C1100](fatal-error-c1100.md)|Nepodařilo se inicializovat OLE: *chyba*|
|Závažná chyba C1101|nejde vytvořit obslužnou rutinu pro atribut '*identifikátor*.|
|Závažná chyba C1102|nepovedlo se inicializovat: *chyba*|
|[Závažná chyba C1103](fatal-error-c1103.md)|Závažná chyba při importu progid: "*zpráva*.|
|[Závažná chyba C1104](fatal-error-c1104.md)|Závažná chyba při importu libid: "*zpráva*.|
|Závažná chyba C1105|*zpráva*: *chyba*|
|[Závažná chyba C1107](../../error-messages/compiler-errors-1/fatal-error-c1107.md)|nepovedlo se najít sestavení "*sestavení*': Zadejte cesty pro hledání sestavení pomocí parametru /AI nebo nastavením proměnné prostředí LIBPATH|
|[Závažná chyba C1108](fatal-error-c1108.md)|nejde najít DLL: "*souboru*.|
|[Závažná chyba C1109](fatal-error-c1109.md)|nepovedlo se najít "*symbol*"v knihovně DLL'*souboru*"|
|Závažná chyba C1110|příliš mnoho vnořené šablony nebo generické definice|
|Závažná chyba C1111|příliš mnoho parametrů šablony nebo generické|
|Závažná chyba C1112|limit kompilátoru: `'number`"příliš mnoho argumentů makra; je pouze *číslo* povoleno|
|[Závažná chyba C1113](../../error-messages/compiler-errors-1/fatal-error-c1113.md)|#using selhalo na '*souboru*.|
|Závažná chyba C1114|"*souboru*": WinRT nepodporuje #using spravovaného sestavení|
|[Závažná chyba C1120](../../error-messages/compiler-errors-1/fatal-error-c1120.md)|Volání GetProcAddress selhalo pro "*funkce*.|
|[Závažná chyba C1121](../../error-messages/compiler-errors-1/fatal-error-c1121.md)|volání CryptoAPI selhalo.|
|[Závažná chyba C1126](../../error-messages/compiler-errors-1/fatal-error-c1126.md)|automatické přidělování překračuje *velikost*|
|[Závažná chyba C1128](../../error-messages/compiler-errors-1/fatal-error-c1128.md)|počet oddílů překročil limit formátu souboru objektu: zkompilujte s možností/bigobj|
|[Závažná chyba C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)|#error: *zprávy*|
|[Závažná chyba C1190](fatal-error-c1190.md)|spravovaný cílený kód vyžaduje "/ clr: možnost|
|[Závažná chyba C1191](../../error-messages/compiler-errors-1/fatal-error-c1191.md)|"*souboru*" se dají importovat jenom u globálního rozsahu|
|[Závažná chyba C1192](../../error-messages/compiler-errors-1/fatal-error-c1192.md)|#using selhalo na '*souboru*.|
|Závažná chyba C1193|byl očekáván chybu v *souboru*(*řádku*) nebylo dosaženo|
|Závažná chyba C1195|použití parametru /Yu a /Yc na stejném příkazovém řádku není kompatibilní s parametrem/CLR.|
|[Závažná chyba C1196](fatal-error-c1196.md)|"*identifikátor*': identifikátor našel v knihovně typů '*typelib*" není platný identifikátor C++|
|[Závažná chyba C1197](../../error-messages/compiler-errors-1/fatal-error-c1197.md)|nemůže odkazovat na "*souboru*'protože program už odkazuje na"*souboru*.|
|[Závažná chyba C1201](fatal-error-c1201.md)|nejde pokračovat po chybě syntaxe v definici šablony třídy.|
|[Závažná chyba C1202](fatal-error-c1202.md)|rekurzivní typ nebo kontext závislosti funkce příliš složitý.|
|[Závažná chyba C1205](fatal-error-c1205.md)|Obecné typy nejsou podporovány verzí modulu runtime nainstalovaného|
|[Závažná chyba C1206](fatal-error-c1206.md)|Data na úrovni appdomain není podporovaná ve verzi modulu runtime nainstalovaného|
|[Závažná chyba C1207](fatal-error-c1207.md)|Spravované šablony nejsou podporované ve verzi modulu runtime nainstalovaný|
|[Závažná chyba C1208](fatal-error-c1208.md)|Přidělení referenčních tříd pro zásobník není podporovaná ve verzi modulu runtime nainstalovaného|
|[Závažná chyba C1209](fatal-error-c1209.md)|Sestavení Friend nejsou podporovaná ve verzi modulu runtime nainstalovaný|
|[Závažná chyba C1210](fatal-error-c1210.md)|/ CLR: pure a/CLR: safe nejsou podporované ve verzi modulu runtime nainstalovaný|
|[Závažná chyba C1211](fatal-error-c1211.md)|Vlastní atribut TypeForwardedTo není podporován verzí modulu runtime nainstalovaného|
|Závažná chyba C1300|Chyba při přístupu k databázi programu *souboru* (*zpráva*)|
|Závažná chyba C1301|Chyba při přístupu k databázi programu *souboru*, neplatný formát, odstraňte prosím a znovu sestavte|
|Závažná chyba C1302|žádná data profilu pro modul '*modulu*'v databázi profilu"*souboru*.|
|[Závažná chyba C1305](../../error-messages/compiler-errors-1/fatal-error-c1305.md)|profilové databáze "*souboru*" je pro jinou architekturu.|
|Závažná chyba C1306|Poslední změna dat profilu základní "*souboru*' nebyla analýza optimalizace; optimalizační rozhodnutí už můžou být zastaralá.|
|[Závažná chyba C1307](../../error-messages/compiler-errors-1/fatal-error-c1307.md)|Program byl upraven od shromáždění dat profilu|
|[Závažná chyba C1308](../../error-messages/compiler-errors-1/fatal-error-c1308.md)|*soubor*: propojování sestavení není podporováno.|
|[Závažná chyba C1309](../../error-messages/compiler-errors-1/fatal-error-c1309.md)|Neshoda verzí C2. Knihovny DLL a pgodb*ver*. KNIHOVNY DLL|
|[Závažná chyba C1310](fatal-error-c1310.md)|optimalizace na základě profilu nejsou s OpenMP dostupné.|
|[Závažná chyba C1311](../../error-messages/compiler-errors-1/fatal-error-c1311.md)|Formát COFF nemůže staticky inicializovat "*symbol*" s *číslo* b adresy.|
|[Závažná chyba C1312](fatal-error-c1312.md)|Moc velký počet podmíněných větví ve funkci.  Zjednodušte nebo Refaktorujte zdrojový kód.|
|[Závažná chyba C1313](../../error-messages/compiler-errors-1/fatal-error-c1313.md)|limit kompilátoru: *typ* bloky nemůžou být vnořené hlouběji než *číslo* úrovně|
|[Závažná chyba C1350](../../error-messages/compiler-errors-1/fatal-error-c1350.md)|Chyba při načítání knihovny dll '*souboru*': knihovna dll nebyla nalezena|
|[Závažná chyba C1351](../../error-messages/compiler-errors-1/fatal-error-c1351.md)|Chyba při načítání knihovny dll '*souboru*': nekompatibilní verze|
|[Závažná chyba C1352](fatal-error-c1352.md)|Neplatný nebo poškozený kód MSIL ve funkci '*funkce*"z modulu'*modulu*"|
|[Závažná chyba C1353](fatal-error-c1353.md)|Operace metadat se nepovedla: modul runtime není nainstalovaný nebo nesouhlasí jeho verze|
|[Závažná chyba C1382](../../error-messages/compiler-errors-1/fatal-error-c1382.md)|soubor PCH "*souboru*"byla znovu sestavena od"*obj*' byla vygenerována. Změňte prosím tento objekt|
|[Závažná chyba C1383](fatal-error-c1383.md)|– možnost kompilátoru /GL je nekompatibilní s nainstalovanou verzí modulu common language runtime|
|Závažná chyba C1384|Nesprávné nastavení pgo_path_translation při propojování "*souboru*.|
|Závažná chyba C1451|Nepovedlo se vygenerovat informace o ladění při kompilování grafu volání pro: concurrency::parallel_for_each: "*callsite*.|
|Závažná chyba C1505|neopravitelné analyzátor dopředného vyhledávání chyby|
|[Závažná chyba C1506](../../error-messages/compiler-errors-1/fatal-error-c1506.md)|Chyba při vytváření oboru neopravitelné bloku|
|[Závažná chyba C1508](fatal-error-c1508.md)|limit kompilátoru: "*funkce*': více než 65 535 bajtů argumentu|
|[Závažná chyba C1509](../../error-messages/compiler-errors-1/fatal-error-c1509.md)|limit kompilátoru: moc velký počet stavů obslužná rutina výjimky ve funkci '*funkce*"; Zjednodušte funkci|
|[Závažná chyba C1510](../../error-messages/compiler-errors-1/fatal-error-c1510.md)|Nejde otevřít jazykový prostředek clui.dll.|
|[Závažná chyba C1601](../../error-messages/compiler-errors-1/fatal-error-c1601.md)|operační kód nepodporované vloženého sestavení|
|[Závažná chyba C1602](../../error-messages/compiler-errors-1/fatal-error-c1602.md)|Nepodporovaný vnitřní typ|
|[Závažná chyba C1603](../../error-messages/compiler-errors-1/fatal-error-c1603.md)|cíl větve vloženého sestavení mimo rozsah o *číslo* bajtů|
|[Závažná chyba C1852](fatal-error-c1852.md)|"*souboru*' není platný předkompilovaného hlavičkového souboru|
|[Závažná chyba C1853](../../error-messages/compiler-errors-1/fatal-error-c1853.md)|"*souboru*" soubor předkompilované hlavičky je z předchozí verze kompilátoru, nebo předkompilované hlavičky je C++ a vy ji používáte z C (nebo naopak)|
|[Závažná chyba C1854](../../error-messages/compiler-errors-1/fatal-error-c1854.md)|nejde zapsat informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: "*souboru*.|
|[Závažná chyba C1900](../../error-messages/compiler-errors-1/fatal-error-c1900.md)|IL – Neshoda mezi "*nástroj*'version'*číslo*"a"*nástroj*'version'*číslo*.|
|Závažná chyba C1901|Vnitřní chyba správy paměti|
|[Závažná chyba C1902](../../error-messages/compiler-errors-1/fatal-error-c1902.md)|Neshoda správce databáze programu; Zkontrolujte si prosím instalaci|
|[Závažná chyba C1903](fatal-error-c1903.md)|nejde obnovit z přechozích chyb; kompilace se zastavuje|
|[Závažná chyba C1904](fatal-error-c1904.md)|interakce se špatným zprostředkovatelem: "*souboru*.|
|[Závažná chyba C1905](../../error-messages/compiler-errors-1/fatal-error-c1905.md)|Front-endu a back-end není kompatibilní (musí cílit na stejný procesor).|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md)
