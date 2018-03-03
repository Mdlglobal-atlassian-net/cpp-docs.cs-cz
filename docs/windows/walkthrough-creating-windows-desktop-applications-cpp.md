---
title: "Návod: Vytvoření tradiční aplikace Windows Desktop (C++) | Microsoft Docs"
ms.custom: 
ms.date: 1/11/2018
ms.reviewer: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce3c18abbace2181b2d31e0621b6e376021be68a
ms.sourcegitcommit: c2e990450ccd528d85b2783fbc63042612987cfd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2018
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Návod: Vytvoření tradiční aplikace Windows Desktop (C++)

Tento návod ukazuje, jak vytvořit tradiční desktopová aplikace systému Windows v sadě Visual Studio. Ukázková aplikace, které vytvoříte pomocí rozhraní API systému Windows zobrazí "Hello, Windows desktop!" v okně. Můžete použít kód, který budete vyvíjet v tomto názorném postupu jako vzor k vytvoření dalších aplikací klasické pracovní plochy Windows.

Rozhraní API systému Windows (také označované jako Win32 API, rozhraní API systému Windows Desktop a klasické rozhraní API systému Windows) je rozhraní na základě jazyka C pro vytváření aplikací pro Windows. Ho byla v existence od 1980s a byla použita k vytvoření aplikace systému Windows pro dekád. Pokročilé a jednodušší programu rozhraní mají byl postavený na toto rozhraní API, například MFC, ATL a rozhraní .NET Framework. I tím většina moderních kódu pro aplikace UWP a úložiště napsané v jazyce C + +/ WinRT používá toto rozhraní API pod. Další informace o rozhraní API systému Windows najdete v tématu [Index rozhraní API systému Windows](https://msdn.microsoft.com/library/windows/desktop/ff818516.aspx). Existuje mnoho způsobů, jak vytvořit aplikace systému Windows, ale byla první.

> [!IMPORTANT]
> Některé příkazy kódu jsou z důvodu jako stručný výtah vynechání v textu. [Sestavte kód](#build-the-code) zobrazuje kompletní kód na konci tohoto dokumentu.

## <a name="prerequisites"></a>Požadavky

- Počítače se systémem Microsoft Windows 7 nebo novější verze. Pro dosažení co nejlepších výsledků vývoj doporučujeme Windows 10.

- Kopie Visual Studio 2017. Informace o tom, jak stáhnout a nainstalovat Visual Studio najdete v tématu [nainstalovat Visual Studio 2017](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že **vývoj aplikací s jazykem C++** zatížení je zaškrtnuté. Nebojte se, pokud jste nenainstalovali tímto zatížením, při instalaci sady Visual Studio. Můžete znovu spusťte instalační program a nainstalujte jej.

   ![Vývoj aplikací s jazykem C++](../build/media/desktop-development-with-cpp.png "vývoj aplikací s C++")

- Seznámíte se základy používání prostředí Visual Studio IDE. Pokud jste použili aplikacích klasické pracovní plochy Windows před, můžete pravděpodobně udržovat. Úvod najdete v části [prohlídka funkce Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Pochopení dostatek základy jazyka C++ se podle nich zorientujete. Nemusíte si dělat starosti, provedeme nemáte nic nenastavujte příliš komplikovaný.

## <a name="create-a-windows-desktop-project"></a>Vytvoření projektu plochy Windows

Postupujte podle těchto kroků vytvořte svůj první projekt plochy Windows a zadejte kód pro pracovní plochy aplikace systému Windows. Pokud používáte verzi sady Visual Studio, které jsou starší než Visual Studio 2017 verze 15.3, přeskočit na [k vytvoření projektu plochy Windows ve Visual Studio 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Vytvoření projektu plochy Windows Visual Studio 2017 aktualizace 15.3 a novější

1. Na **soubor** nabídce zvolte **nový** a potom zvolte **projektu**.

1. V **nový projekt** dialogové okno, v levém podokně rozbalte **nainstalovaná**, **Visual C++**, pak vyberte **Windows Desktop**. V prostředním podokně vyberte **Windows Desktop průvodce**.

   V **název** pole, zadejte název projektu, například *DesktopApp*. Zvolte **OK**.

   ![Název projektu DesktopApp](../build/media/desktop-app-new-project-name-153.png "název projektu DesktopApp")

1. V **projektu pro Windows Desktop** dialogové okno, v části **typ aplikace**, vyberte **aplikací systému Windows (.exe)**. V části **další možnosti**, vyberte **prázdný projekt**. Zvolte **OK** a vytvořte tak projekt.

   ![V systému Windows Desktop projektu průvodce vytvořit DesktopApp](../build/media/desktop-app-new-project-wizard-153.png "vytvořit DesktopApp v systému Windows Desktop projektu průvodce")

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **DesktopApp** projektu, zvolte **přidat**a potom zvolte **novou položku**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "přidat novou položku do projektu DesktopApp")

1. V **přidat novou položku** dialogové okno, vyberte **soubor C++ ()**. V **název** pole, zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **přidat**.

   ![Přidat souboru do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "souboru přidat do projektu DesktopApp")

Nyní vytvoření projektu a váš zdrojový soubor se otevře v editoru. Chcete-li pokračovat, přejděte rovnou na [vytvořit kód](#create-the-code).

### <a id="create-in-vs2017-rtm"></a>Vytvoření projektu plochy Windows ve Visual Studio 2017 RTM

1. Na **soubor** nabídce zvolte **nový** a potom zvolte **projektu**.

1. V **nový projekt** dialogové okno, v levém podokně rozbalte **nainstalovaná**, **šablony**, **Visual C++**a potom vyberte **Win32**. V prostředním podokně vyberte **projektu Win32**.

   V **název** pole, zadejte název projektu, například *DesktopApp*. Zvolte **OK**.

   ![Název projektu DesktopApp](../build/media/desktop-app-new-project-name-150.png "název projektu DesktopApp")

1. Na **přehled** stránky **Win32 – Průvodce aplikací**, zvolte **Další**.

   ![Vytvoření DesktopApp v Win32 – Průvodce aplikací – přehled](../build/media/desktop-app-win32-wizard-overview-150.png "vytvořit DesktopApp v Win32 – Průvodce aplikací – přehled")

1. Na **nastavení aplikace** v části **typ aplikace**, vyberte **aplikace Windows**. V části **další možnosti**, vyberte **prázdný projekt**. Zvolte **Dokončit** a vytvořte tak projekt.

   ![V nastavení Průvodce aplikace Win32 vytvořit DesktopApp](../build/media/desktop-app-win32-wizard-settings-150.png "vytvořit DesktopApp v nastavení Průvodce aplikace Win32")

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt DesktopApp, zvolte **přidat**a potom zvolte **novou položku**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "přidat novou položku do projektu DesktopApp")

1. V **přidat novou položku** dialogové okno, vyberte **soubor C++ ()**. V **název** pole, zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **přidat**.

   ![Přidat souboru do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "souboru přidat do projektu DesktopApp")

Nyní vytvoření projektu a váš zdrojový soubor se otevře v editoru.

## <a name="create-the-code"></a>Vytváření kódu

Dále budete zjistěte, jak vytvořit kód pro aplikace Windows v sadě Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Spuštění aplikace Windows

1. Stejně jako všechny C musí mít aplikace a aplikace C++ `main` fungovat jako výchozí bod, každý Windows desktop aplikace musí mít `WinMain` funkce. `WinMain`má následující syntaxi.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Informace o parametry a návratové hodnoty této funkce najdete v tématu [WinMain vstupní bod](https://msdn.microsoft.com/library/windows/desktop/ms633559).

   > [!NOTE]
   > Co jsou všechny tyto doplňující slova, například **zpětného volání**, nebo **HINSTANCE**, nebo  **\_v\_**? Tradiční rozhraní API systému Windows používá – definice TypeDef a makra preprocesoru hojně k abstraktní rychle některé podrobnosti typů a specifické pro platformu kódu, jako například volání konvence, **__declspec** deklarace a direktivy kompilátoru. V sadě Visual Studio, můžete použít IntelliSense [rychlé informace](/visualstudio/ide/using-intellisense#quick-info) funkce, které chcete zobrazit, co tyto definice TypeDef a makra definovat. Umístěte ukazatel myši nad slovo, které vás zajímají, nebo ji vyberte a stiskněte klávesu ctrl-K, ctrl-I pro malý místní okno, který obsahuje definici. Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense). Parametry a návratové typy často používají *poznámek SAL* vám pomohou catch programování chyby. Další informace najdete v tématu [použití poznámek SAL k snížení závad kódu C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Desktopové programy Windows vyžadují &lt;odkazující na Windows >. &lt;Tchar.h > definuje `TCHAR` makro, který se nakonec přeloží na `wchar_t` Pokud je symbol UNICODE je definována v projektu, jinak se přeloží na `char`.  Pokud vytvoříte vždy s povoleným kódem UNICODE, nepotřebujete Tchar – a právě wchar_t přímo použít.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Kromě `WinMain` funkce, každá aplikace Windows desktop musí mít také funkci proceduru okna. Tato funkce je obvykle s názvem `WndProc` , ale můžete pojmenovat se vám líbí. `WndProc`má následující syntaxi.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   V této funkci můžete psát kód pro zpracování *zprávy* přijímající aplikace z Windows při *události* dojít. Například pokud se uživatel rozhodne tlačítko OK v aplikaci, systém Windows bude pro vás posílat zprávy a můžete napsat kód uvnitř vaší `WndProc` funkce, která aktivují pracovní je vhodné. To se označuje jako *zpracování* událost. Zpracováváte jenom události, které jsou relevantní pro vaši aplikaci.

   Další informace najdete v tématu [procedury oken](https://msdn.microsoft.com/library/windows/desktop/ms632593).

### <a name="to-add-functionality-to-the-winmain-function"></a>Přidání funkce do WinMain – funkce

1. V `WinMain` funkce, naplnit struktura typu [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577). Tato struktura obsahuje informace o okně, například ikona aplikace, barvu pozadí období, název se má zobrazit v záhlaví a co je velmi důležité, ukazatel na funkci procedury okna. Následující příklad ukazuje typické `WNDCLASSEX` struktura.

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   Informace o polích tuto strukturu najdete v tématu [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577).

1. Je nutné zaregistrovat `WNDCLASSEX` se systémem Windows, aby věděl, že IT oddělení může o okně aplikace a jak odesílat zprávy. Použití [RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587) funkce a předejte strukturu třídy okna jako argument. `_T` Makro je použít, protože používáme `TCHAR` typu.

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. Nyní můžete vytvořit okno. Použití [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679) funkce.

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   Funkce vrátí hodnotu `HWND`, což je popisovač pro okno. Popisovač je něco jako ukazatel, které používá systém Windows ke sledování otevřete windows. Další informace najdete v tématu [Windows datové typy](https://msdn.microsoft.com/library/windows/desktop/aa383751).

1. V tomto okamžiku okno vytvořila, ale musíme v systému Windows zviditelnit nastavit. To je, jaké tento kód:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Okno zobrazené nemá množství obsahu, protože nebyla ještě implementována `WndProc` funkce. Jinými slovy aplikace není ještě zpracování zprávy, které je nyní odesílání systému Windows.

1. Pro zpracování zprávy, nejprve přidáme zpráva smyčky přijímat zprávy, které systém Windows odešle. Když aplikace obdrží zprávu, tento smyčky odešle ji do vašeho `WndProc` funkce zpracovávat. Zpráva smyčky se podobá následující kód.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Další informace týkající se struktury a funkcí ve smyčce zpráv najdete v tématu [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958), [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936), [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955), a [DispatchMessage ](https://msdn.microsoft.com/library/windows/desktop/ms644934).

   V tomto okamžiku `WinMain` funkce by měla vypadat přibližně následující kód.

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>Přidání funkce do WndProc – funkce

1. Chcete-li povolit `WndProc` funkce pro zpracování zprávy, které aplikace obdrží, implementovat příkazu switch.

   Jeden důležité zpráva pro zpracování [WM_PAINT](https://msdn.microsoft.com/library/windows/desktop/dd145213) zprávy. Aplikace obdrží tuto zprávu při součástí jeho zobrazit okno se musí aktualizovat. Tato událost může dojít, když uživatel přesune časového období před okně aplikace, a poté přesunut, ho znovu. Aplikace není známo, když dojde k událostmi, jako je to; zná pouze systém Windows, tak se zobrazí oznámení s `WM_PAINT`. Pokud se nejprve zobrazí okno, musíte aktualizovat všechny.

   Pro zpracování `WM_PAINT` zprávy, první volání [BeginPaint –](https://msdn.microsoft.com/library/windows/desktop/dd183362), pak zpracování všechnu logiku pro rozložení textu, tlačítek a jiných ovládacích prvků v okně a pak zavolají [EndPaint –](https://msdn.microsoft.com/library/windows/desktop/dd162598). Pro tuto aplikaci logiky mezi volání počáteční a koncovou volání se zobrazí řetězec "Hello, Windows desktop!" v okně. V následujícím kódu, Všimněte si, že [TextOut](https://msdn.microsoft.com/library/windows/desktop/dd145133) funkce se používá k zobrazení řetězec.

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC`Tento kód je popisovač pro kontext zařízení, což je datová struktura, která Windows používá k aktivaci aplikace ke komunikaci s grafiky subsystému. `BeginPaint` a `EndPaint` funkce zajistěte, aby vaše aplikace se chová jako dobrý občanem a nepoužívá kontextu zařízení po delší dobu, než je potřeba. To pomáhá zajistit, že grafický subsystém je k dispozici pro použití jinými aplikacemi.

1. Aplikace obvykle zpracovává mnoho dalších zpráv, například [WM_CREATE](https://msdn.microsoft.com/library/windows/desktop/ms632619) při prvním vytvoření okna a [WM_DESTROY](https://msdn.microsoft.com/library/windows/desktop/ms632620) při zavření okna. Následující kód ukazuje základní ale Dokončit `WndProc` funkce.

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>Sestavte kód

Jak dohodnutými, zde je kompletní kód funkční aplikaci.

### <a name="to-build-this-example"></a>K vytvoření v tomto příkladu

1. Odstraňte žádný kód, který jste zadali v HelloWindowsDesktop.cpp v editoru. Tento příklad kódu zkopírujte a vložte jej do HelloWindowsDesktop.cpp:

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. Na **sestavení** nabídce zvolte **sestavit řešení**. Výsledky kompilace by se měla objevit v **výstup** oken v sadě Visual Studio.

   ![Sestavení projektu DesktopApp](../build/media/desktop-app-project-build-150.gif "sestavení projektu DesktopApp")

1. Chcete-li spustit nástroj, stiskněte **F5**. Okno, které obsahuje text "Hello, Windows desktop!" by se zobrazit v levém horním rohu obrazovky.

   ![Spusťte projekt DesktopApp](../build/media/desktop-app-project-run-150.gif "spusťte projekt DesktopApp")

Blahopřejeme! Dokončení tohoto průvodce a vytvořené tradiční aplikace pracovní plochy Windows.

## <a name="see-also"></a>Viz také

[Aplikace pracovní plochy Windows](../windows/windows-desktop-applications-cpp.md)
