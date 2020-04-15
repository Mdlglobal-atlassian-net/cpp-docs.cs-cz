---
title: Ukázkový projekt Jazyka C++ pro analýzu kódu
description: Jak vytvořit ukázkové řešení pro použití v návodu analýzy kódu pro Microsoft C++ v sadě Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: c2a1b8c80b7e7aebd1f1530c66ade5859b392028
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372064"
---
# <a name="sample-c-project-for-code-analysis"></a>Ukázkový projekt Jazyka C++ pro analýzu kódu

Následující postupy ukazují, jak vytvořit ukázku pro [návod: Analýza kódu C/C++ pro vady](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Postupy vytvářejí:

- Řešení sady Visual Studio s názvem *CppDemo*.

- Projekt statické knihovny s názvem *CodeDefects*.

- Projekt statické knihovny s názvem *Poznámky*.

Procedury také poskytují kód pro soubory záhlaví a *CPP* pro statické knihovny.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Vytvoření řešení CppDemo a projektu CodeDefects

::: moniker range=">=vs-2019"

1. Otevření Visual Studia a výběr **možnosti Vytvořit nový projekt**

1. V **dialogovém** okně Vytvořit nový projekt změňte filtr jazyka na **C++**.

1. Vyberte **Průvodce plochu systému Windows** a zvolte tlačítko **Další.**

1. Na stránce **Konfigurovat nový projekt** zadejte do textového pole Název **projektu** *kód Vady*.

1. Do textového pole **Název řešení** zadejte *CppDemo*.

1. Zvolte **Vytvořit**.

1. V dialogovém okně **Projekt plochy systému Windows** změňte typ **aplikace** na **Static Kál (.lib).**

1. V části **Další možnosti**vyberte **Možnost Prázdný projekt**.

1. Chcete-li vytvořit řešení a projekt, zvolte **OK.**

::: moniker-end

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V dialogovém okně **Nový projekt** vyberte **Visual C++** > **Windows Desktop**.

1. Vyberte **Průvodce plochou windows**.

1. Do textového pole **Název** zadejte *KódVady*.

1. Do textového pole **Název řešení** zadejte *CppDemo*.

1. Vyberte **OK**.

1. V dialogovém okně **Projekt plochy systému Windows** změňte typ **aplikace** na **Static Kál (.lib).**

1. V části **Další možnosti**vyberte **Možnost Prázdný projekt**.

1. Chcete-li vytvořit řešení a projekt, zvolte **OK.**

::: moniker-end

::: moniker range="vs-2015"

1. Otevřete sadu Visual Studio. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V dialogovém okně **Nový projekt** vyberte **šablony** > **Visual C++** > **Win32**.

1. Vyberte **win32 konzolové aplikace**.

1. Do textového pole **Název** zadejte *KódVady*.

1. Do textového pole **Název řešení** zadejte *CppDemo*.

1. Vyberte **OK**.

1. V dialogovém okně **Průvodce aplikací win32** zvolte tlačítko **Další.**

1. Změňte **typ aplikace** na **statickou knihovnu**.

1. V části **Další možnosti**zrušte výběr **možnosti Předkompilované záhlaví**.

1. Chcete-li vytvořit řešení a projekt, zvolte **Dokončit.**

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Přidání hlavičkového a zdrojového souboru do projektu CodeDefects

1. V Průzkumníku řešení rozbalte **codedefects**.

1. Klepnutím pravým tlačítkem myši otevřete místní nabídku **pro soubory hlaviček**. Zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** > **Code**a pak vyberte Soubor **záhlaví (.h).**

1. Do pole **Name** edit zadejte *Bug.h*a pak zvolte **tlačítko Přidat.**

1. V editačním okně pro *Bug.h*vyberte a odstraňte obsah.

1. Zkopírujte následující kód a vložte jej do souboru *Bug.h* v editoru.

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. Klepnutím pravým tlačítkem myši otevřete v Průzkumníkovi řešení místní nabídku **zdrojových souborů**. Zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**.

1. Do pole **Name** edit zadejte *Bug.cpp*a pak zvolte **tlačítko Přidat.**

1. Zkopírujte následující kód a vložte jej do souboru *Bug.cpp* v editoru.

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. Na řádku nabídek zvolte **Soubor** > **Uložit vše**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Přidání projektu Poznámky a jeho konfigurace jako statické knihovny

::: moniker range=">=vs-2019"

1. V Průzkumníku řešení otevřete místní nabídku klepnutím pravým tlačítkem myši na **příkaz CppDemo.** Zvolte **Přidat** > **nový projekt**.

1. V **dialogovém** okně Přidat nový projekt vyberte **Průvodce plochu systému Windows**a pak zvolte tlačítko **Další.**

1. Na stránce **Konfigurovat nový projekt** zadejte do textového pole Název **projektu** *poznámky*a pak zvolte **Vytvořit**.

1. V dialogovém okně **Projekt plochy systému Windows** změňte typ **aplikace** na **Static Kál (.lib).**

1. V části **Další možnosti**vyberte **Možnost Prázdný projekt**.

1. Chcete-li vytvořit projekt, zvolte **OK.**

::: moniker-end

::: moniker range="vs-2017"

1. V Průzkumníku řešení otevřete místní nabídku klepnutím pravým tlačítkem myši na **příkaz CppDemo.** Zvolte **Přidat** > **nový projekt**.

1. V dialogovém okně **Přidat nový projekt** vyberte Visual **C++** > **Windows Desktop**.

1. Vyberte **Průvodce plochou windows**.

1. Do textového pole **Název** zadejte *poznámky*a pak zvolte **OK**.

1. V dialogovém okně **Projekt plochy systému Windows** změňte typ **aplikace** na **Static Kál (.lib).**

1. V části **Další možnosti**vyberte **Možnost Prázdný projekt**.

1. Chcete-li vytvořit projekt, zvolte **OK.**

::: moniker-end

::: moniker range="vs-2015"

1. V Průzkumníku řešení otevřete místní nabídku klepnutím pravým tlačítkem myši na **příkaz CppDemo.** Zvolte **Přidat** > **nový projekt**.

1. V dialogovém okně **Přidat nový projekt** vyberte Visual **C++** > **Win32**.

1. Vyberte **win32 konzolové aplikace**.

1. Do textového pole **Název** zadejte *poznámky*.

1. Vyberte **OK**.

1. V dialogovém okně **Průvodce aplikací win32** zvolte tlačítko **Další.**

1. Změňte **typ aplikace** na **statickou knihovnu**.

1. V části **Další možnosti**zrušte výběr **možnosti Předkompilované záhlaví**.

1. Chcete-li vytvořit projekt, zvolte **Dokončit.**

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Přidání souboru záhlaví a zdrojového souboru do projektu Poznámky

1. V Průzkumníku řešení **rozbalte poznámky**.

1. Klepnutím pravým tlačítkem myši otevřete místní nabídku **pro soubory hlaviček** v části **Poznámky**. Zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** > **Code**a pak vyberte Soubor **záhlaví (.h).**

1. Do pole **Name** edit zadejte *anotations.h*a pak zvolte tlačítko **Přidat.**

1. V editačním okně pro *anotace.h*vyberte a odstraňte obsah.

1. Zkopírujte následující kód a vložte jej do souboru *anotace.h* v editoru.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. Klepnutím pravým tlačítkem myši otevřete v Průzkumníkovi řešení místní nabídku **zdrojových souborů** v části **Poznámky**. Zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**.

1. Do pole **Name** edit zadejte *anotations.cpp*a pak zvolte tlačítko **Přidat.**

1. Zkopírujte následující kód a vložte jej do souboru *anotations.cpp* v editoru.

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. Na řádku nabídek zvolte **Soubor** > **Uložit vše**.

Řešení je nyní dokončeno a mělo by být sestavení bez chyb.

::: moniker range="vs-2017"

> [!NOTE]
> V sadě Visual Studio 2017 se může `E1097 unknown attribute "no_init_all"` zobrazit falešné upozornění v modulu IntelliSense. Toto upozornění můžete klidně ignorovat.

::: moniker-end
