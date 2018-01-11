---
title: Kompilace programu C++ pro CLR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: "40"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eca6960d23c43fbe27d753ab4f79a27dea7bd7e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Návod: Kompilace programu C++ pro CLR v aplikaci Visual Studio
Můžete vytvořit programy Visual C++, které používají rozhraní .NET třídy a jejich kompilace pomocí vývojovém prostředí sady Visual Studio.  
  
 Pro tento postup můžete zadat vlastní program Visual C++, nebo použijte jednu z ukázkové aplikace. Ukázkový program, který používáme v tomto postupu vytvoří textový soubor s názvem textfile.txt a uloží ho do adresáře projektu.  
  
## <a name="prerequisites"></a>Požadavky  
 V těchto tématech předpokládají, že rozumíte základy jazyka C++.  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Vytvořte nový projekt v sadě Visual Studio a přidat nový soubor zdroje  
  
1.  Vytvořte nový projekt. Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.  
  
2.  Typy projektu Visual C++, klikněte na tlačítko **CLR**a potom klikněte na **prázdný projekt CLR**.  
  
3.  Zadejte název projektu.  
  
     Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění pro projekt.  
  
     Klikněte na tlačítko **OK** k vytvoření nového projektu.  
  
4.  Průzkumník řešení se nezobrazí, klikněte na tlačítko **Průzkumníku řešení** na **zobrazení** nabídky.  
  
5.  Přidejte nové zdrojového souboru do projektu:  
  
    -   Klikněte pravým tlačítkem myši **zdrojové soubory** složky v Průzkumníku řešení, přejděte na **přidat** a klikněte na tlačítko **novou položku**.  
  
    -   Klikněte na tlačítko **soubor C++ ()** a zadejte název souboru a pak klikněte na tlačítko **přidat**.  
  
     **Sada** souboru se zobrazí v **zdrojové soubory** složka v Průzkumníku řešení a okno s kartami se zobrazí, kde zadáte kód chcete v tomto souboru.  
  
6.  Klikněte na kartě nově vytvořený v sadě Visual Studio a zadejte platný program Visual C++, nebo zkopírujte a vložte jednu z ukázkové aplikace.  
  
     Například můžete použít [postupy: zápis do textového souboru (C + +/ CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) ukázka programu (v **zpracování souborů a vstupně-výstupních operací** uzlu Průvodce programováním).  
  
     Pokud používáte ukázkový program, Všimněte si, že používáte `gcnew` – klíčové slovo místo `new` při vytváření objektu .NET a že `gcnew` vrací popisovač (`^`) namísto ukazatele (`*`):  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     Další informace o nové syntaxe jazyka Visual C++, najdete v části [rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).  
  
7.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     **Výstup** okně se zobrazí informace o průběhu kompilace, jako je například umístění protokolu sestavení a zprávu, která označuje stav sestavení.  
  
     Pokud provedete změny a spustit program bez provedení sestavení, dialogové okno může znamenat, že projekt je zastaralý. Zaškrtněte políčko v tomto dialogovém okně, před kliknutím na **OK** Pokud chcete vždy používat aktuální verze souborů místo zobrazení výzvy vždy, když chcete sestavení aplikace.  
  
8.  Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
9. Pokud jste použili ukázkový program, když spustíte program, který se zobrazí okno příkazového řádku, který označuje, že byl vytvořen soubor text. Stisknutím libovolné klávesy zavřete příkazové okno.  
  
     **Textfile.txt** textový soubor se nyní nachází v adresáři projektu. Tento soubor můžete otevřít v programu Poznámkový blok.  
  
    > [!NOTE]
    >  Výběr prázdný CLR šablona projektu automaticky nastaví **/CLR** – možnost kompilátoru. Chcete-li to ověřit, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a kliknutím na **vlastnosti**a potom zkontrolujte **podpory Common Language Runtime** možnost  **Obecné** uzlu **vlastnosti konfigurace**.  
  
## <a name="whats-next"></a>Co je další  
 **Předchozí:** [návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **Další:**[návod: kompilace programu v jazyce C na příkazovém řádku](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)