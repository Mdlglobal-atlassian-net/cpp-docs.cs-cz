---
title: 'Postupy: uspořádání výstupních souborů projektu pro sestavení | Microsoft Docs'
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
ms.openlocfilehash: 5058493e93a89e64c87ef52b73ff8fe3272f8f99
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705342"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Postupy: Uspořádání výstupních souborů projektu pro sestavení
Toto téma popisuje osvědčené postupy pro uspořádání výstupních souborů projektu. Sestavení při nesprávně nastavíte výstupních souborů projektu, může dojít k chybám. Toto téma také popisuje výhody a nevýhody jednotlivých možností uspořádání výstupních souborů projektu.  
  
## <a name="referencing-clr-assemblies"></a>Odkazování na sestavení CLR  
  
#### <a name="to-reference-assemblies-with-using"></a>Odkazování na sestavení pomocí #using  
  
1.  Odkazování na sestavení přímo z vašeho kódu pomocí #using – direktiva, jako například `#using <System.Data.dll>`. Další informace najdete v tématu [#using – direktiva](../preprocessor/hash-using-directive-cpp.md).  
  
     Zadaný soubor může být .dll, .exe, .netmodule nebo .obj, dokud je v MSIL. Odkazovaná součást se dají vytvářet v libovolném jazyce. Použití této možnosti budete mít přístup technologie IntelliSense, protože metadata se extrahují z MSIL. V souboru musí být v cestě pro projekt; jinak nebude kompilace projektu a IntelliSense nebudete mít k dispozici. Snadný způsob, jak určit, zda je soubor v cestě je klikněte pravým tlačítkem na #using řádku a vyberte **otevřít dokument** příkaz. Pokud soubor nelze nalézt, budete upozorněni.  
  
     Pokud nechcete uvést úplnou cestu k souboru, můžete použít **/AI** – možnost kompilátoru upravit cestu pro hledání #using. Další informace najdete v tématu [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md).  
  
#### <a name="to-reference-assemblies-with-fu"></a>Odkazování na sestavení pomocí /FU  
  
1.  Namísto odkazování na sestavení přímo ze souboru kódu, jak je popsáno výše, můžete použít **/FU** – možnost kompilátoru. Výhodou této metody je, že není nutné přidat samostatné # příkaz using pro každý soubor, který odkazuje na dané sestavení.  
  
     Pokud chcete nastavit tuto možnost, otevřete **vlastnosti stránky** pro projekt. Rozbalte **vlastnosti konfigurace** uzel a potom rozbalte **C/C++** uzel a vyberte možnost **Upřesnit**. Přidejte požadované sestavení do **Force #using**. Další informace najdete v tématu [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md).  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>Odkazování na sestavení s přidat nový odkaz  
  
1.  Toto je nejjednodušší způsob, jak používat sestavení CLR. První, ujistěte se, že kompilace projektu s **/CLR** – možnost kompilátoru. Potom klikněte pravým tlačítkem na projekt z **Průzkumníku řešení** a vyberte **přidat**, **odkazy**. **Stránky vlastností** zobrazí se dialogové okno.  
  
2.  Z **stránky vlastností** dialogovém okně, vyberte **přidat nový odkaz**. Zobrazí se dialogové okno se zobrazí seznam všech rozhraní .NET, COM a ostatních sestavení, které jsou dostupné v aktuálním projektu. Vyberte požadované sestavení a klikněte na tlačítko **OK**.  
  
     Jakmile je nastavená odkaz na projekt, jsou zpracovávány automaticky odpovídající závislosti. Navíc vzhledem k tomu, že metadata jsou součástí sestavení, je nutné přidat soubory hlaviček nebo spravovat prvky, které jsou používány ze spravovaných sestavení.  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>Odkazování na nativních knihoven DLL nebo statické knihovny  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>Chcete-li nativních knihoven DLL nebo statické knihovny  
  
1.  Odkaz na příslušný soubor hlaviček v kódu pomocí #include – direktiva. Soubor hlaviček musí být v cestě zahrnout nebo součástí aktuálního projektu. Další informace najdete v tématu [#include – direktiva (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).  
  
2.  Můžete také nastavit závislosti projektu. Nastavení závislostí projektu zaručuje dvě věci. Nejprve zajišťuje sestavení projektů ve správném pořadí, aby projektu vždy najít závislé soubory, které potřebuje. Druhý implicitně přidá závislé projektu výstupní adresář do cesty tak, aby soubory lze snadno nalézt v době propojení.  
  
3.  Pokud chcete nasadit aplikaci, musíte umístit knihovnu DLL do správného umístění. To může být jeden z následujících akcí:  
  
    1.  Stejnou cestu jako spustitelný soubor.  
  
    2.  Kdekoli v cestě k systému souborů ( **cesta** proměnnou prostředí).  
  
    3.  V souběžně sdílená sestavení. Další informace najdete v tématu [sestavení C/C++-souběžného sestavení](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="working-with-multiple-projects"></a>Práce s více projekty  
 Ve výchozím nastavení projekty jsou vytvořeny tak, aby všechny výstupní soubory se vytvoří v podadresáři adresáře projektu. Má adresář název v závislosti na konfiguraci sestavení (např. ladění a vydání). Aby na stejné úrovni projekty k odkazování na sobě navzájem musíte každý projekt explicitně přidat další adresáře projektu výstup do jejich cesty v pořadí pro úspěšné propojení. To se provádí automaticky při nastavení závislosti projektu. Ale pokud nepoužijete závislosti, je nutné pečlivě zajistit to protože sestavení se může stát velmi obtížné spravovat. Například když na projekt má konfigurace Debug a Release a obsahuje vnější knihovny z projektu na stejné úrovni, by měl použít soubor různé knihovny, podle toho, která je sestavena konfigurace. Pevně kódováno tyto cesty proto může být složité.  
  
 Všechny základní výstupní soubory (například spustitelné soubory, soubory přírůstkové linkeru a soubory PDB) se zkopírují do společný adresář řešení. Proto při práci s řešením, který obsahuje počet projekty C++ se stejnou konfigurací, jsou všechny výstupní soubory centralizované pro zjednodušené propojení a nasazení. Můžete si být jisti, že jejich aplikace/knihovna bude fungovat podle očekávání, pokud tyto soubory zůstanou společně (protože soubory jsou zaručena bezpečnost pro přístup v cestě).  
  
 Umístění výstupu souborů může být závažný problém při nasazení v produkčním prostředí. Při spouštění projekty v prostředí IDE, cesty k zahrnuté knihovny, nemusí nutně být stejné jako v provozním prostředí. Pokud máte například `#using "../../lib/debug/mylib.dll"` ve vašem kódu, ale pak nasadíte mylib jinou relativní pozici, aplikace se nezdaří za běhu. Chcete-li tomu zabránit, neměli byste používat relativní cesty v #include příkazů v kódu. Je lepší zajistit potřebné soubory v cestě sestavení projektu a podobně zajistit, že odpovídající provozní soubory jsou umístěny správně.  
  
#### <a name="how-to-specify-where-output-files-go"></a>Určení umístění výstupních souborů  
  
1.  Umístění projektu výstup, nastavení se dají najít v projektu **stránky vlastností**. Rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. Výstupní umístění je zadaný do **výstupního adresáře**. Další informace najdete v tématu [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md).  
  
## <a name="see-also"></a>Viz také  
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)