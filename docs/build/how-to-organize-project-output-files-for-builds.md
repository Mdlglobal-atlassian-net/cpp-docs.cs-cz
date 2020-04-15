---
title: 'Postupy: Uspořádání výstupních souborů projektu pro sestavení'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
ms.openlocfilehash: 13aa3d1f8e2993ca34163ecbc0515948db56eb79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328532"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Postupy: Uspořádání výstupních souborů projektu pro sestavení

Toto téma popisuje osvědčené postupy pro uspořádání výstupních souborů projektu. Chyby sestavení může dojít při nastavení výstupnísoubory projektu nesprávně. Toto téma také popisuje výhody a nevýhody každé alternativy pro uspořádání výstupních souborů projektu.

## <a name="referencing-clr-assemblies"></a>Odkazování na sestavení CLR

#### <a name="to-reference-assemblies-with-using"></a>Odkazna sestavy s #using

1. Můžete odkazovat na sestavení přímo z kódu pomocí `#using <System.Data.dll>`direktivy #using, například . Další informace naleznete [v #using směrnice](../preprocessor/hash-using-directive-cpp.md).

   Zadaný soubor může být .dll, .exe, .netmodule nebo .obj, pokud je v MSIL. Odkazovanou komponentu lze sestavit v libovolném jazyce. Pomocí této možnosti budete mít přístup k intelliSense, protože metadata budou extrahována z MSIL. Daný soubor musí být v cestě k projektu; v opačném případě se projekt nezkompiluje a technologie IntelliSense nebude k dispozici. Snadný způsob, jak zjistit, zda je soubor v cestě, je kliknout pravým tlačítkem myši na řádek #using a zvolit příkaz **Otevřít dokument.** Pokud soubor nelze najít, budete upozorněni.

   Pokud nechcete umístit úplnou cestu k souboru, můžete použít možnost kompilátoru **/AI** k úpravě cesty hledání pro #using odkazy. Další informace naleznete [v tématu /AI (Zadejte adresáře metadat)](reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Odkazna sestavy s /FU

1. Namísto odkazování na sestavení přímo ze souboru kódu, jak je popsáno výše, můžete použít možnost kompilátoru **/FU.** Výhodou této metody je, že není třeba přidávat samostatný příkaz #using ke každému souboru, který odkazuje na dané sestavení.

   Chcete-li tuto možnost nastavit, otevřete **stránky vlastností** projektu. Rozbalte uzel **Vlastnosti konfigurace,** rozbalte uzel **C/C++** a vyberte **Upřesnit**. Přidejte požadovaná sestavení vedle **položky Force #using**. Další informace naleznete v tématu [/FU (Name Forced #using File).](reference/fu-name-forced-hash-using-file.md)

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Odkazna sestavení pomocí přidat nový odkaz

1. Toto je nejjednodušší způsob použití sestav CLR. Nejprve se ujistěte, že je projekt zkompilován pomocí možnosti kompilátoru **/clr.** Potom klepněte pravým tlačítkem myši na projekt z **Průzkumníka řešení** a vyberte **přidat**, **odkazy**. Zobrazí se dialogové okno **Stránky vlastností.**

1. V dialogovém okně **Stránky vlastností** vyberte **Přidat nový odkaz**. Zobrazí se dialogové okno se seznamem všech sestavení .NET, COM a dalších sestavení dostupných v aktuálním projektu. Vyberte požadovanou sestavu a klepněte na **OK**.

   Po nastavení odkazu na projekt jsou automaticky zpracovány odpovídající závislosti. Kromě toho vzhledem k tomu, že metadata jsou součástí sestavení, není nutné přidávat soubor záhlaví nebo prototyp prvků, které jsou používány ze spravovaných sestavení.

## <a name="referencing-native-dlls-or-static-libraries"></a>Odkazování na nativní knihovny DLL nebo statické knihovny

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Odkazna nativní knihovny DLL nebo statické knihovny

1. Odkazna příslušný soubor záhlaví v kódu pomocí #include směrnice. Soubor záhlaví musí být v cestě zahrnutí nebo v části aktuálního projektu. Další informace naleznete [v tématu #include směrnice (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Můžete také nastavit závislosti projektu. Nastavení závislostí projektu zaručuje dvě věci. Nejprve zajišťuje, že projekty jsou sestaveny ve správném pořadí tak, aby projekt může vždy najít závislé soubory, které potřebuje. Za druhé implicitně přidá výstupní adresář závislého projektu do cesty, aby bylo možné soubory snadno najít v době propojení.

1. Chcete-li nasadit aplikaci, budete muset umístit dll na vhodném místě. To může být jeden z následujících:

   1. Stejná cesta jako spustitelný soubor.

   1. Kdekoli v systémové cestě (proměnná prostředí **cesty).**

   1. V sestavě vedle sebe. Další informace naleznete [v tématu Building C/C++ Side-by-side Assemblies](building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Práce s více projekty

Ve výchozím nastavení jsou projekty vytvořeny tak, aby všechny výstupní soubory byly vytvořeny v podadresáři adresáře projektu. Adresář je pojmenován na základě konfigurace sestavení (např. ladění nebo vydání). Aby na sebe měly vzájemně odkazovat projekty na stejné úrovni, musí každý projekt explicitně přidat další výstupní adresáře projektu do své cesty, aby bylo propojení úspěšné. To se provádí automaticky při nastavení závislostí projektu. Pokud však nepoužíváte závislosti, je nutné pečlivě zpracovat, protože sestavení může být velmi obtížné spravovat. Například pokud projekt má ladění a uvolnění konfigurace a obsahuje externí knihovnu z projektu na stejné úrovni, by měl použít jiný soubor knihovny v závislosti na konfiguraci, která je právě sestavována. Takže tvrdé kódování těchto cest může být složité.

Všechny základní výstupní soubory (například spustitelné soubory, přírůstkové propojovací soubory a soubory PDB) jsou zkopírovány do společného adresáře řešení. Proto při práci s řešením, které obsahuje řadu projektů jazyka C++ s ekvivalentní konfigurace, všechny výstupní soubory jsou centralizovány pro zjednodušené propojení a nasazení. Můžete si být jisti, že jejich aplikace nebo knihovna bude fungovat podle očekávání, pokud udržují tyto soubory pohromadě (protože soubory jsou zaručeně v cestě).

Umístění výstupních souborů může být hlavní problém při nasazování do produkčního prostředí. Při spuštění projektů v ide, cesty k zahrnuté knihovny nejsou nutně stejné jako v produkčním prostředí. Například pokud máte `#using "../../lib/debug/mylib.dll"` v kódu, ale pak nasadit mylib.dll do jiné relativní pozice, aplikace se nezdaří za běhu. Chcete-li tomu zabránit, měli byste se vyhnout použití relativní cesty v příkazech #include v kódu. Je lepší zajistit, že potřebné soubory jsou v cestě sestavení projektu a podobně zajistit, že odpovídající produkční soubory jsou správně umístěny.

#### <a name="how-to-specify-where-output-files-go"></a>Jak určit, kam výstupní soubory jdou

1. Umístění nastavení výstupu projektu naleznete na stránkách **vlastností**projektu . Rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. Výstupní umístění je určeno vedle **výstupního adresáře**. Další informace naleznete [v tématu General Property Page (Project)](reference/general-property-page-project.md).

## <a name="see-also"></a>Viz také

[Typy projektů Jazyka C++ v sadě Visual Studio](reference/visual-cpp-project-types.md)
