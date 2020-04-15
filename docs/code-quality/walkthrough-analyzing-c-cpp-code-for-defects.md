---
title: 'Návod: Analýza kódu C/C++ pro vady'
description: Ukazuje, jak používat analýzu kódu s Microsoft C++ v sadě Visual Studio.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370206"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Návod: Analýza kódu C/C++ pro vady

Tento návod ukazuje, jak analyzovat kód C/C++ pro potenciální vady kódu. Používá nástroje pro analýzu kódu C/C++.

V tomto návodu:

- Spusťte analýzu kódu v nativním kódu.
- Analyzovat upozornění na vady kódu.
- Považovat upozornění za chybu.
- Osušte zdrojový kód pro zlepšení analýzy vad kódu.

## <a name="prerequisites"></a>Požadavky

- Kopie [CppDemo vzorku](../code-quality/demo-sample.md).
- Základní znalost c/c++.

## <a name="run-code-analysis-on-native-code"></a>Spuštění analýzy kódu v nativním kódu

### <a name="to-run-code-defect-analysis-on-native-code"></a>Spuštění analýzy vad kódu v nativním kódu

::: moniker range=">=vs-2019"

1. Otevřete řešení CppDemo v sadě Visual Studio.

     Řešení CppDemo nyní naplňuje **Průzkumníka řešení**.

1. V nabídce **Sestavení** zvolte **Znovu sestavit řešení**.

     Řešení se staví bez chyb nebo upozornění.

1. V **Průzkumníku řešení**vyberte projekt CodeDefects.

1. V nabídce **Projekt** zvolte **Vlastnosti**.

     Zobrazí se dialogové okno **Stránky vlastností Vady** kódu.

1. Vyberte stránku **vlastností Analýza kódu.**

1. Změňte **vlastnost Povolit analýzu kódu při sestavení na** **Ano**. Chcete-li uložit změny, zvolte **OK.**

1. Znovu sestavit codedefects projektu.

     Upozornění analýzy kódu jsou zobrazena v okně **Seznam chyb.**

::: moniker-end

::: moniker range="<=vs-2017"

1. Otevřete řešení CppDemo v sadě Visual Studio.

     Řešení CppDemo nyní naplňuje **Průzkumníka řešení**.

1. V nabídce **Sestavení** zvolte **Znovu sestavit řešení**.

     Řešení se staví bez chyb nebo upozornění.

     > [!NOTE]
     > V sadě Visual Studio 2017 se může `E1097 unknown attribute "no_init_all"` zobrazit falešné upozornění v modulu IntelliSense. Toto upozornění můžete klidně ignorovat.

1. V **Průzkumníku řešení**vyberte projekt CodeDefects.

1. V nabídce **Projekt** zvolte **Vlastnosti**.

     Zobrazí se dialogové okno **Stránky vlastností Vady** kódu.

1. Vyberte stránku **vlastností Analýza kódu.**

1. Zaškrtněte políčko **Povolit analýzu kódu v sestavení.** Chcete-li uložit změny, zvolte **OK.**

1. Znovu sestavit codedefects projektu.

     Upozornění analýzy kódu jsou zobrazena v okně **Seznam chyb.**

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>Analýza upozornění na vady kódu

1. V nabídce **View** zvolte **Error List**.

     Tato položka nabídky nemusí být viditelná. Záleží na profilu vývojáře, který jste zvolili v sadě Visual Studio. V nabídce **Zobrazení** bude pravděpodobně třeba přejděte na **položku Jiný systém Windows** a potom zvolte **Seznam chyb**.

1. V okně **Seznam chyb** poklepejte na následující upozornění:

     C6230: Implicitní přetypované mezi sémanticky různé typy: pomocí HRESULT v logickém kontextu.

     Editor kódu zobrazí řádek, který způsobil `bool ProcessDomain()`upozornění uvnitř funkce . Toto upozornění `HRESULT` označuje, že a se používá v příkazu if, kde se očekává logický výsledek. Je to obvykle chyba, protože `S_OK` když HRESULT je vrácena z funkce označuje úspěch, ale při převodu na logickou hodnotu vyhodnotí na `false`.

1. Opravte toto `SUCCEEDED` upozornění pomocí makra, které se převede na `true` hodnotu, pokud vrácená `HRESULT` hodnota označuje úspěch. Váš kód by se měl podobat následujícímu kódu:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. V **seznamu chyb**poklepejte na následující upozornění:

     C6282: Nesprávný operátor: přiřazení konstanty v logickém kontextu. Zvažte použití '==' místo.

1. Opravte toto upozornění testováním rovnosti. Váš kód by měl vypadat podobně jako následující kód:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Opravte zbývající upozornění C6001 v **seznamu** `i` chyb `j` inicializací a na 0.

1. Znovu sestavit codedefects projektu.

     Projekt se staví bez upozornění nebo chyb.

## <a name="correct-source-code-annotation-warnings"></a>Správná upozornění na poznámky zdrojového kódu

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>Povolení upozornění na poznámky zdrojového kódu v anotaci.c

::: moniker range=">=vs-2019"

1. V Průzkumníku řešení vyberte projekt Poznámky.

1. V nabídce **Projekt** zvolte **Vlastnosti**.

     Zobrazí se dialogové okno **Stránky vlastností anotací.**

1. Vyberte stránku **vlastností Analýza kódu.**

1. Změňte **vlastnost Povolit analýzu kódu při sestavení na** **Ano**. Chcete-li uložit změny, zvolte **OK.**

::: moniker-end

::: moniker range="<=vs-2017"

1. V Průzkumníku řešení vyberte projekt Poznámky.

1. V nabídce **Projekt** zvolte **Vlastnosti**.

     Zobrazí se dialogové okno **Stránky vlastností anotací.**

1. Vyberte stránku **vlastností Analýza kódu.**

1. Zaškrtněte políčko **Povolit analýzu kódu v sestavení.** Chcete-li uložit změny, zvolte **OK.**

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Oprava upozornění na poznámky zdrojového kódu v anotaci.c

1. Znovu vytvořte projekt poznámky.

1. V nabídce **Build** zvolte **Spustit analýzu kódu u anotací**.

1. V **seznamu chyb**poklepejte na následující upozornění:

     C6011: Dereferencing NULL ukazatel 'newNode'.

     Toto upozornění označuje selhání volajícího zkontrolovat vrácenou hodnotu. V takovém případě může `AllocateNode` volání vrátit hodnotu NULL. V souboru záhlaví anotations.h naleznete `AllocateNode`deklaraci funkce pro aplikaci .

1. Kurzor je na umístění v souboru anotations.cpp, kde došlo k upozornění.

1. Chcete-li opravit toto upozornění, použijte příkaz if k testování vrácené hodnoty. Váš kód by se měl podobat následujícímu kódu:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Znovu vytvořte projekt poznámky.

     Projekt se staví bez upozornění nebo chyb.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Použití poznámky zdrojového kódu ke zjištění dalších problémů

### <a name="to-use-source-code-annotation"></a>Použití poznámky zdrojového kódu

1. Anotovat formální parametry a vrácená `AddTail` hodnota funkce k označení hodnoty ukazatele může být null:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. V nabídce **Build** zvolte **Spustit analýzu kódu v řešení**.

1. V **seznamu chyb**poklepejte na následující upozornění:

     C6011: Dereferencing NULL ukazatel 'uzel'.

     Toto upozornění znamená, že uzel předaný do funkce může být null.

1. Chcete-li opravit toto upozornění, použijte příkaz if na začátku funkce k testování hodnoty, která byla předána. Váš kód by se měl podobat následujícímu kódu:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. V nabídce **Build** zvolte **Spustit analýzu kódu v řešení**.

     Projekt se nyní staví bez upozornění nebo chyb.

## <a name="see-also"></a>Viz také

[Návod: Analýza spravovaného kódu pro vady kódu](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
