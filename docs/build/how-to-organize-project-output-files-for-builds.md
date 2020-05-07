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

Toto téma popisuje osvědčené postupy pro uspořádání výstupních souborů projektu. Chyby sestavení mohou nastat při nesprávném nastavení výstupních souborů projektu. Toto téma také popisuje výhody a nevýhody jednotlivých alternativ pro uspořádání výstupních souborů projektu.

## <a name="referencing-clr-assemblies"></a>Odkazování na sestavení CLR

#### <a name="to-reference-assemblies-with-using"></a>Odkazování na sestavení pomocí #using

1. Můžete odkazovat na sestavení přímo z kódu pomocí direktivy #using, jako je například `#using <System.Data.dll>`. Další informace najdete v tématu [direktiva #using](../preprocessor/hash-using-directive-cpp.md).

   Zadaný soubor může být. dll,. exe,. netmodule nebo. obj, pokud je v jazyce MSIL. Odkazovaná komponenta může být sestavena v jakémkoli jazyce. Pomocí této možnosti budete mít přístup k IntelliSense, protože metadata budou extrahována z jazyka MSIL. Daný soubor musí být v cestě pro projekt. v opačném případě projekt nebude zkompilován a IntelliSense nebude k dispozici. Snadný způsob, jak určit, zda je soubor v cestě, je kliknout pravým tlačítkem na #using řádek a zvolit příkaz **otevřít dokument** . Pokud se soubor nenajde, zobrazí se oznámení.

   Pokud nechcete zadat úplnou cestu k souboru, můžete použít možnost kompilátoru **/AI** pro úpravu cesty hledání #using odkazů. Další informace najdete v tématu [/AI (určení adresářů metadat)](reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Odkazování na sestavení pomocí/FU

1. Namísto odkazování na sestavení přímo ze souboru kódu, jak je popsáno výše, můžete použít možnost kompilátoru **/Fu** . Výhodou této metody je, že nemusíte přidávat samostatný příkaz #using do každého souboru, který odkazuje na dané sestavení.

   Chcete-li nastavit tuto možnost, otevřete **stránky vlastností** projektu. Rozbalte uzel **Vlastnosti konfigurace** a potom rozbalte uzel **C/C++** a vyberte **Upřesnit**. Přidejte požadovaná sestavení vedle **vynucení #using**. Další informace najdete v tématu [/Fu (název vynuceného #using souboru)](reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>Odkazování na sestavení pomocí přidání nového odkazu

1. Toto je nejjednodušší způsob, jak použít sestavení CLR. Nejprve se ujistěte, že je projekt kompilován pomocí možnosti kompilátoru **/CLR** . Pak klikněte pravým tlačítkem myši na projekt z **Průzkumník řešení** a vyberte **Přidat**, **odkazy**. Zobrazí se dialogové okno **stránky vlastností** .

1. V dialogovém okně **stránky vlastností** vyberte možnost **Přidat nový odkaz**. Zobrazí se dialogové okno se seznamem všech sestavení .NET, COM a dalších sestavení dostupných v aktuálním projektu. Vyberte požadované sestavení a klikněte na tlačítko **OK**.

   Jakmile je odkaz na projekt nastaven, odpovídající závislosti jsou automaticky zpracovány. Kromě toho, vzhledem k tomu, že metadata jsou součástí sestavení, není nutné přidávat hlavičkový soubor ani prototypovat prvky, které jsou používány ze spravovaných sestavení.

## <a name="referencing-native-dlls-or-static-libraries"></a>Odkazování na nativní knihovny DLL nebo statické knihovny

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Odkazování na nativní knihovny DLL nebo statické knihovny

1. Odkazujte na příslušný hlavičkový soubor v kódu pomocí direktivy #include. Hlavičkový soubor musí být v cestě include nebo v rámci aktuálního projektu. Další informace naleznete v tématu [direktiva #include (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Můžete také nastavit závislosti projektu. Nastavení závislostí projektu zaručuje dvě věci. Za prvé zajistí, že projekty jsou sestaveny ve správném pořadí tak, aby projekt mohl vždy najít závislé soubory, které potřebuje. Za druhé implicitně přidá do cesty výstupní adresář závislého projektu, aby bylo možné soubory v době propojování snadno najít.

1. Chcete-li nasadit aplikaci, bude nutné umístit knihovnu DLL na příslušné místo. Může to být jedna z následujících možností:

   1. Stejná cesta jako spustitelný soubor.

   1. Kdekoli v systémové cestě (proměnná prostředí **path** ).

   1. V souběžném sestavení. Další informace naleznete v tématu sestavení [souběžných sestavení C/C++](building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Práce s více projekty

Ve výchozím nastavení jsou projekty sestaveny tak, že všechny výstupní soubory jsou vytvořeny v podadresáři adresáře projektu. Adresář je pojmenován na základě konfigurace sestavení (například ladění nebo vydání). Aby projekty na stejné úrovni odkazovaly na sebe navzájem, každý projekt musí explicitně přidat výstupní adresáře ostatních projektů do jejich cesty, aby bylo propojení úspěšné. To se provádí automaticky při nastavování závislostí projektu. Nicméně pokud nepoužíváte závislosti, je nutné pečlivě zpracovat, protože sestavení mohou být velmi obtížné spravovat. Například pokud má projekt konfiguraci ladění a vydání a obsahuje externí knihovnu z projektu na stejné úrovni, měl by použít jiný soubor knihovny v závislosti na tom, která konfigurace je právě sestavena. Proto může být pevně zakódovaných cest obtížné.

Všechny podstatné výstupní soubory (například spustitelné soubory, přírůstkové soubory linkeru a soubory PDB) se zkopírují do společného adresáře řešení. Proto při práci s řešením, které obsahuje několik projektů C++ se stejnými konfiguracemi, jsou všechny výstupní soubory centralizované pro zjednodušené propojování a nasazování. Můžete si být jisti, že aplikace nebo knihovna budou fungovat podle očekávání, pokud je tyto soubory pohromadě (vzhledem k tomu, že jsou soubory v cestě zaručeny).

Umístění výstupních souborů může být zásadním problémem při nasazení do provozního prostředí. Při spouštění projektů v integrovaném vývojovém prostředí nejsou cesty zahrnuté knihovny nutně stejné jako v produkčním prostředí. Například pokud máte `#using "../../lib/debug/mylib.dll"` ve svém kódu, ale pak nasadíte mylib. dll do jiné relativní pozice, aplikace se za běhu nezdaří. Chcete-li tomu zabránit, měli byste se vyhnout používání relativních cest v příkazech #include ve vašem kódu. Je lepší zajistit, aby byly potřebné soubory v cestě sestavení projektu, a podobně zajistit správné umístění odpovídajících produkčních souborů.

#### <a name="how-to-specify-where-output-files-go"></a>Jak určit, kde se mají výstupní soubory přejít

1. Umístění výstupního nastavení projektu lze nalézt na **stránkách vlastností**projektu. Rozbalte uzel vedle **Možnosti konfigurační vlastnosti** a vyberte **Obecné**. Umístění výstupu je zadané vedle **výstupního adresáře**. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](reference/general-property-page-project.md).

## <a name="see-also"></a>Viz také

[Typy projektů C++ v aplikaci Visual Studio](reference/visual-cpp-project-types.md)
