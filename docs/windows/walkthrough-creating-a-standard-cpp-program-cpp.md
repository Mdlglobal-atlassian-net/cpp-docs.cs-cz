---
title: 'Návod: Vytvoření standardního programu C++ (C++) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vcfirstapp
- vccreatefirst
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac1fac3c7f96c9f8d718efa54810f4155b1ddac5
ms.sourcegitcommit: c0ffdff538eb961f786809eb547b35846190ee48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2018
ms.locfileid: "34800083"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Návod: Vytvoření standardního programu C++ (C++)
Visual C++ v sadě Visual Studio integrované vývojové prostředí (IDE) slouží k vytvoření standardní C++ – programy. Podle kroků v tomto návodu, můžete vytvořit projekt, přidejte do projektu nový soubor, úpravou souboru přidejte kód C++ a pak zkompilování a spuštění programu pomocí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Můžete zadat vlastní programu C++ nebo použijte jednu z ukázkové aplikace. Ukázkový program v tomto návodu je konzolová aplikace. Tato aplikace používá `set` kontejneru ve standardní knihovně C++.  
  
 Visual C++ v souladu s 2003 Standard C++, s následujícími hlavními výjimkami: vyhledání názvu dvoufázová, specifikace výjimek a export. Kromě toho Visual C++ podporuje několik funkcí C ++ 0 x, například lambdas, automaticky, static_assert, odkazy rvalue a externí šablony.  
  
> [!NOTE]
>  Pokud je třeba kompatibilita se standardem, **/Za** – možnost kompilátoru zakázat rozšíření Microsoft pro standardní. Další informace najdete v tématu [/Za, /Ze (zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Předpokladem práce s tímto návodem je znalost základů jazyka C++.  
  
### <a name="to-create-a-project-and-add-a-source-file"></a>Vytvoření projektu a přidání zdrojového souboru  
  
1.  Vytvoření projektu tak, že odkazuje na **nový** na **soubor** nabídce a potom kliknutím na **projektu**.  
  
2.  V **Visual C++** projektu typy podokně, klikněte na tlačítko **Windows Desktop**a potom klikněte na **konzolové aplikace pro Windows**.  
  
3.  Zadejte název projektu.  
  
     Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění pro projekt.  
  
     Klikněte na tlačítko **OK** a vytvořte tak projekt.  
  
4.  Pokud **Průzkumníku řešení** se nezobrazí na **zobrazení** nabídky, klikněte na tlačítko **Průzkumníku řešení**.  
  
5.  Přidejte nové zdrojového souboru do projektu, následujícím způsobem.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **zdrojové soubory** složku, přejděte na příkaz **přidat**a potom klikněte na **novou položku**.  
  
    2.  V **kód** uzel, klikněte na tlačítko **soubor C++ ()**, zadejte název souboru a pak klikněte na tlačítko **přidat**.  
  
     Souboru se zobrazí ve složce zdrojové soubory v **Průzkumníku**, a soubor se otevře v editoru Visual Studio.  
  
6.  V souboru v editoru zadejte platný programu C++, který používá standardní knihovna C++ nebo jedna z ukázkových aplikací zkopírujte a vložte ji v souboru.  
  
7.  Uložte soubor.  
  
8. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     **Výstup** okně se zobrazí informace o průběhu kompilace, například umístění protokolu sestavení a zprávu, která označuje stav sestavení.  
  
9. Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.  
  
     Pokud jste použili ukázkový program, zobrazí se okno příkazového řádku a zobrazuje, zda určitá celá čísla se nacházejí v sadě.  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [Konzolová aplikace v jazyce Visual C++](../windows/console-applications-in-visual-cpp.md). **Další krok:**[návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
