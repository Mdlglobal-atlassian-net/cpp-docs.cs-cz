---
title: 'Návod: Analýza kódu CC++ /v případě vad'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: 5fbdf9e223b3c1e1b8664de2018381958c458f45
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77418653"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Návod: Analýza kódu CC++ /v případě vad

Tento návod ukazuje, jak analyzovat kód CC++ /Code pro potenciální nedostatky v kódu pomocí nástroje Analýza kódu pro C/C++ Code.

- Spusťte analýzu kódu v nativním kódu.
- Analyzuje upozornění na vady kódu.
- Považovat upozornění za chybu.
- Opatřit zdrojový kód poznámkami, aby se zlepšila analýza vad kódu.

## <a name="prerequisites"></a>Předpoklady

- Kopie [ukázkové ukázky](../code-quality/demo-sample.md).
- Základní porozumění C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Spuštění analýzy vad kódu v nativním kódu

1. Otevřete ukázkové řešení v aplikaci Visual Studio.

     Ukázkové řešení nyní naplňuje **Průzkumník řešení**.

1. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.

     Řešení se sestaví bez chyb nebo upozornění.

1. V **Průzkumník řešení**vyberte projekt CodeDefects.

1. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

     Zobrazí se dialogové okno **stránky vlastností CodeDefects** .

1. Klikněte na **Analýza kódu**.

1. Klikněte na zaškrtávací políčko **Povolit analýzu kódu proC++ sestavení C/on** .

1. Znovu sestavte projekt CodeDefects.

     Upozornění analýzy kódu se zobrazují v **Seznam chyb**.

### <a name="to-analyze-code-defect-warnings"></a>Analýza upozornění na vady kódu

1. V nabídce **zobrazení** klikněte na příkaz **Seznam chyb**.

     V závislosti na profilu vývojáře, který jste zvolili v aplikaci Visual Studio, bude pravděpodobně nutné Ukázat na **jiné okna** v nabídce **zobrazení** a pak kliknout na tlačítko **Seznam chyb**.

1. V **Seznam chyb**dvakrát klikněte na následující upozornění:

     Upozornění C6230: implicitní přetypování mezi sémanticky odlišnými typy: používá HRESULT v logickém kontextu.

     Editor kódu zobrazuje řádek, který způsobil upozornění ve funkci `bool ProcessDomain()`. Toto upozornění indikuje, že `HRESULT` se používá v příkazu if, kde se očekává logický výsledek.  Obvykle se jedná o chybu, protože když se vrátí `S_OK` HRESULT z funkce IT, je indikována úspěch, ale když se převede na logickou hodnotu, vyhodnotí se jako `false`.

1. Opravte toto upozornění pomocí makra `SUCCEEDED`, které se převede na `true`, když `HRESULT` návratová hodnota indikuje úspěch. Váš kód by měl vypadat podobně jako následující kód:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

1. V **Seznam chyb**dvakrát klikněte na následující upozornění:

     Warning C6282: nesprávný operátor: přiřazení k konstantě v kontextu testu. Bylo = = zamýšleno?

1. Opravte toto upozornění pomocí testování rovnosti. Váš kód by měl vypadat podobně jako následující kód:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Zpracování upozornění jako chyby

1. V souboru Error. cpp přidejte následující příkaz `#pragma` na začátek souboru, aby se upozornění C6001 jako chyba:

   ```cpp
   #pragma warning (error: 6001)
   ```

1. Znovu sestavte projekt CodeDefects.

     V **Seznam chyb**se teď jako chyba zobrazuje C6001.

1. Opravte zbývající dvě chyby C6001 v **Seznam chyb** inicializací `i` a `j` na 0.

1. Znovu sestavte projekt CodeDefects.

     Projekt se vytváří bez upozornění a chyb.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Oprava upozornění pro poznámky zdrojového kódu v poznámce. c

1. V Průzkumník řešení vyberte projekt poznámky.

1. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

     Zobrazí se dialogové okno **stránky vlastností poznámky** .

1. Klikněte na **Analýza kódu**.

1. Zaškrtněte zaškrtávací políčko **Povolit analýzu kódu pro sestaveníC++ C/on** .

1. Znovu sestavte projekt poznámky.

1. V **Seznam chyb**dvakrát klikněte na následující upozornění:

     Upozornění C6011: přesměrování NULOVÉho ukazatele "newNode".

     Toto upozornění signalizuje selhání volajícímu, aby zkontroloval vrácenou hodnotu. V takovém případě volání **AllocateNode** může vracet hodnotu null (viz hlavičkový soubor poznámky. h pro deklaraci funkce pro AllocateNode).

1. Otevřete soubor poznámky. cpp.

1. Chcete-li toto upozornění opravit, použijte příkaz if pro otestování návratové hodnoty. Váš kód by měl vypadat podobně jako následující kód:

   ```cpp
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Znovu sestavte projekt poznámky.

     Projekt se vytváří bez upozornění a chyb.

### <a name="to-use-source-code-annotation"></a>Použití poznámky ke zdrojovému kódu

1. Zadáním formálních parametrů a návratové hodnoty funkce `AddTail` označíte, že hodnoty ukazatele mohou být null:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Znovu sestavit projekt poznámek.

1. V **Seznam chyb**dvakrát klikněte na následující upozornění:

     Upozornění C6011: přesměrování NULOVÉho ukazatele "Node".

     Toto upozornění znamená, že uzel předaný do funkce může mít hodnotu null a označuje číslo řádku, kde bylo upozornění vyvoláno.

1. Chcete-li toto upozornění opravit, použijte příkaz if na začátku funkce pro otestování předané hodnoty. Váš kód by měl vypadat podobně jako následující kód:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Znovu sestavit projekt poznámek.

     Projekt se teď sestaví bez jakýchkoli upozornění nebo chyb.

## <a name="see-also"></a>Viz také

[Návod: Analýza spravovaného kódu pro vady kódu](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
