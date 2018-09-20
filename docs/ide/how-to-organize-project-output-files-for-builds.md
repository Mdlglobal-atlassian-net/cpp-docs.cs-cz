---
title: 'Postupy: uspořádání výstupních souborů projektu pro sestavení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f139342e7ccb264d89f9012b8177ff57260f3738
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399792"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Postupy: Uspořádání výstupních souborů projektu pro sestavení

Toto téma popisuje doporučené postupy pro uspořádání výstupních souborů projektu. Sestavení při nastavování výstupních souborů projektu nesprávně, může dojít k chybám. Toto téma také popisuje výhody a nevýhody všech možností uspořádání výstupních souborů projektu.

## <a name="referencing-clr-assemblies"></a>Odkazování na sestavení CLR

#### <a name="to-reference-assemblies-with-using"></a>Odkazování na sestavení pomocí #using

1. Sestavení lze odkazovat přímo v kódu s použitím # direktivy using, jako například `#using <System.Data.dll>`. Další informace najdete v tématu [# direktiva using](../preprocessor/hash-using-directive-cpp.md).

   Zadaný soubor může být .dll, .exe, .netmodule nebo .obj, jako je v jazyce MSIL. Odkazovaná komponenta může být sestavena v libovolném jazyce. Použití této možnosti budete mít přístup k IntelliSense jelikož metadata budou extrahována z jazyka MSIL. Dotyčný soubor musí být v cestě k projektu. jinak projekt nepůjde kompilovat a IntelliSense nebude k dispozici. Snadný způsob, jak zjistit, zda je soubor v cestě je klikněte pravým tlačítkem myši na #using řádku a zvolte **otevřít dokument** příkazu. Pokud nelze najít soubor, budete upozorněni.

   Pokud nechcete vkládat úplnou cestu k souboru, můžete použít **/AI** – možnost kompilátoru pro úpravu vyhledávací cesty pro #using. Další informace najdete v tématu [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>Odkazování na sestavení pomocí /FU

1. Namísto odkazování na sestavení přímo ze souboru kódu, jak je popsáno výše, můžete použít **/FU** – možnost kompilátoru. Výhodou této metody je, že není nutné přidat samostatný # příkaz using pro každý soubor, který odkazuje na dané sestavení.

   Pokud chcete nastavit tuto možnost, otevřete **stránky vlastností** pro projekt. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **C/C++** uzel a vyberte možnost **Upřesnit**. Přidejte požadované sestavení vedle **platnost #using**. Další informace najdete v tématu [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>K odkazování na sestavení pomocí přidat nový odkaz

1. Toto je nejjednodušší způsob použití sestavení CLR. Nejprve zkontrolujte, zda je projekt kompilován s **/CLR** – možnost kompilátoru. Potom klikněte pravým tlačítkem myši klikněte na projekt **Průzkumníku řešení** a vyberte **přidat**, **odkazy**. **Stránky vlastností** zobrazí se dialogové okno.

1. Z **stránky vlastností** dialogového okna, vyberte **přidat nový odkaz**. Dialogové okno se zobrazí seznam všech .NET, COM a jiných sestavení dostupných v aktuálním projektu. Vyberte požadované sestavení a klikněte na tlačítko **OK**.

   Po nastavení projektového odkazu, jsou automaticky zpracovány odpovídající závislosti. Kromě toho protože metadata jsou součástí sestavení, není nutné přidat soubory hlaviček nebo spravovat prvky, které jsou používány ze spravovaných sestavení.

## <a name="referencing-native-dlls-or-static-libraries"></a>Odkazování nativních knihoven DLL nebo statických knihoven

#### <a name="to-reference-native-dlls-or-static-libraries"></a>Odkazování nativních knihoven DLL nebo statických knihoven

1. Odkaz na příslušný soubor hlaviček v kódu pomocí #include. Soubor hlaviček musí být v zahrnutém umístění, nebo část aktuálního projektu. Další informace najdete v tématu [#include – direktiva (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).

1. Můžete také nastavit závislosti projektu. Nastavení závislostí projektu zaručuje dvě věci. Za prvé zajišťuje, že jsou projekty sestaveny ve správném pořadí, takže projekt může vždy najít závislé soubory, které potřebuje. Za druhé implicitně přidá výstupní adresář závislého projektu k cestě tak, aby soubory lze snadno nalézt v době spojení.

1. Pokud chcete nasadit aplikaci, je potřeba umístit knihovnu DLL do správného umístění. Může to být jedna z následujících akcí:

   1. Stejnou cestu jako spustitelný soubor.

   1. Kdekoli v systémových cestách ( **cesta** proměnnou prostředí).

   1. V sestavení vedle sebe. Další informace najdete v tématu [vytváření sestavení C/C++-souběžně](../build/building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Práce s více projekty

Ve výchozím nastavení jsou projekty sestaveny tak, aby všechny výstupní soubory jsou vytvořeny v podadresáři adresáře projektu. Pojmenování tohoto adresáře závisí na konfiguraci sestavení (např. ladění a vydání). V pořadí pro projekty na stejné úrovni jako reference k sobě navzájem musí každý projekt explicitně přidat výstupní adresáře ostatních projektů do svých cest v pořadí pro úspěšné propojení. To se provádí automaticky při nastavení závislostí projektu. Nicméně pokud nepoužijete závislosti, můžete toto nutné pečlivě zpracovat vzhledem k tomu, že sestavení se může stát velmi obtížné spravovat. Například pokud projekt obsahuje konfigurace Debug a Release a zahrnuje externí knihovnu z projektu na stejné úrovni, měla by použít různé soubory knihovny podle toho, která konfigurace je sestavovaná. Pevně kódováno pomocí těchto cest proto může být velmi obtížné.

Všechny základní výstupní soubory (například spustitelné soubory, přírůstkové soubory linkeru a soubory PDB) jsou zkopírovány do společného adresáře řešení. Proto při práci s řešením, která obsahuje několik projektů C++ se stejnou konfigurací, jsou všechny výstupní soubory centralizované pro zjednodušené propojení a nasazení. Můžete si být jisti, že jejich aplikace/knihovna bude fungovat podle očekávání, pokud tyto soubory zůstanou pohromadě (protože soubory jsou zaručeně v cestě).

Umístění výstupních souborů může být závažný problém při nasazení do produkčního prostředí. Při běhu projektů v integrovaném vývojovém prostředí, cesty k načítaným knihovnám nejsou nutně stejné jako v provozním prostředí. Pokud máte například `#using "../../lib/debug/mylib.dll"` ve vašem kódu, ale poté nasadíte mylib.dll do jiného relativního umístění, aplikace selže v době běhu. Chcete-li tomu zabránit, neměli byste používat relativní cesty #include ve vašem kódu. Je lepší zajistěte, aby byly potřebné soubory v cestě sestavení projektu a podobně zajistit, aby odpovídající provozní soubory byly správně umístěny.

#### <a name="how-to-specify-where-output-files-go"></a>Určení umístění výstupních souborů

1. Umístění projektu výstup, nastavení se dají najít v projektu **stránky vlastností**. Rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. Umístění výstupu je určeno **výstupní adresář**. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md).

## <a name="see-also"></a>Viz také

[Typy projektů Visual C++](../ide/visual-cpp-project-types.md)