---
title: 'Návod: Vytvoření tradiční aplikace klasické pracovní plochy Windows (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: fc2080470e3292a459325679a6c5dc00c01d6b35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528375"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Návod: Vytvoření tradiční aplikace klasické pracovní plochy Windows (C++)

Tento návod ukazuje, jak vytvořit tradiční desktopové aplikace Windows v sadě Visual Studio. Ukázková aplikace, které vytvoříte pomocí rozhraní API Windows zobrazí "Hello, plochu Windows!" v okně. Můžete použít kód vyvinutý v tomto názorném postupu jako vzor pro vytvoření jiných aplikací klasické pracovní plochy Windows.

Rozhraní API Windows (označované také jako rozhraní Win32 API, rozhraní API Windows Desktop a Windows klasického rozhraní API) je architektura podle jazyka C pro vytváření aplikací pro Windows. V existence od 1980s a byla použita k vytvoření aplikací Windows desítky let. Pokročilé a jednodušší program rozhraní sestavené nad rámec rozhraní Windows API, jako je například knihovny MFC, ATL a rozhraní .NET Framework. Dokonce i většině moderních kód pro UPW a Store aplikace napsané v jazyce C + +/ WinRT používá rozhraní Windows API pod. Další informace o rozhraní API Windows najdete v tématu [Index rozhraní API Windows](/windows/desktop/apiindex/windows-api-list). Existuje mnoho způsobů, jak vytvářet aplikace pro Windows, ale výše uvedeného postupu byl první.

> [!IMPORTANT]
> Pro účely zkrácení jsou vynechány některé příkazy v textu. [Sestavení kódu](#build-the-code) oddílu na konci tohoto dokumentu obsahuje kompletní kód.

## <a name="prerequisites"></a>Požadavky

- Počítač, na kterém běží Microsoft Windows 7 nebo novější verze. Doporučujeme pro nejlepší vývojové prostředí Windows 10.

- Kopie sady Visual Studio 2017. Informace o tom, jak stáhnout a nainstalovat sadu Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že **vývoj desktopových aplikací pomocí C++** úlohy je zaškrtnuté políčko. Nedělejte si starosti, pokud je tato úloha nenainstaloval při instalaci sady Visual Studio. Můžete znovu spustit instalační program a jeho instalaci.

   ![Vývoj desktopových aplikací pomocí C++](../build/media/desktop-development-with-cpp.png "vývoj desktopových aplikací pomocí C++")

- Znalost základní informace o používání integrovaného vývojového prostředí sady Visual Studio. Pokud jste používali aplikace klasické pracovní plochy Windows před, můžete pravděpodobně udržovat. Úvodní informace najdete v tématu [IDE sady Visual Studio o základních charakteristikách](/visualstudio/ide/visual-studio-ide).

- Pochopení dostatek základy jazyka C++ spolu s příkladem sledovat. Nedělejte si starosti, jsme nic nedělají nic složitého.

## <a name="create-a-windows-desktop-project"></a>Vytvoření projektu klasické pracovní plochy Windows

Postupujte podle následujících kroků vytvořte svůj první projekt klasické pracovní plochy Windows a zadejte kód pro pracovní aplikace klasické pracovní plochy Windows. Pokud používáte verzi sady Visual Studio starší než Visual Studio 2017 verze 15.3, přeskočte k části [vytvořit projekt klasické pracovní plochy Windows v sadě Visual Studio 2017 RTM](#create-in-vs2017-rtm).

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Vytvoření projektu klasické pracovní plochy Windows v sadě Visual Studio 2017 Update 15.3 nebo novější

1. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.

1. V **nový projekt** dialogové okno, v levém podokně rozbalte **nainstalováno** > **Visual C++** a pak vyberte **Windows Desktop**. V prostředním podokně vyberte **desktopový Průvodce pro Windows**.

   V **název** zadejte název projektu, například *DesktopApp*. Zvolte **OK**.

   ![Pojmenujte projekt DesktopApp](../build/media/desktop-app-new-project-name-153.png "pojmenujte projekt DesktopApp")

1. V **Windows desktopový projekt** dialogového okna, v části **typ aplikace**vyberte **aplikace Windows (.exe)**. V části **další možnosti**vyberte **prázdný projekt**. Zvolte **OK** pro vytvoření projektu.

   ![Desktopový projekt Windows pomocí průvodce vytvořit DesktopApp](../build/media/desktop-app-new-project-wizard-153.png "vytvořit DesktopApp v Průvodci desktopový projekt Windows")

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **DesktopApp** projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "přidat novou položku do projektu DesktopApp")

1. V **přidat novou položku** dialogu **soubor C++ (.cpp)**. V **název** zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **přidat**.

   ![Soubor .cpp přidat do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "přidat soubor .cpp DesktopApp projektu")

Váš projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru. Chcete-li pokračovat, přeskočte k části [vytvářet kód](#create-the-code).

### <a id="create-in-vs2017-rtm"></a> Chcete-li vytvořit projekt klasické pracovní plochy Windows v sadě Visual Studio 2017 RTM

1. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.

1. V **nový projekt** dialogové okno, v levém podokně rozbalte **nainstalováno** > **šablony** > **Visual C++** a pak vyberte **Win32**. V prostředním podokně vyberte **projekt Win32**.

   V **název** zadejte název projektu, například *DesktopApp*. Zvolte **OK**.

   ![Pojmenujte projekt DesktopApp](../build/media/desktop-app-new-project-name-150.png "pojmenujte projekt DesktopApp")

1. Na **přehled** stránku **Průvodce aplikací Win32**, zvolte **Další**.

   ![Vytvoření DesktopApp v Přehled Průvodce aplikací Win32](../build/media/desktop-app-win32-wizard-overview-150.png "vytvořit DesktopApp v Přehled Průvodce aplikací Win32")

1. Na **nastavení aplikace** stránce v části **typ aplikace**vyberte **aplikace Windows**. V části **další možnosti**vyberte **prázdný projekt**. Zvolte **Dokončit** pro vytvoření projektu.

   ![Vytvoření DesktopApp v nastavení Průvodce aplikace Win32](../build/media/desktop-app-win32-wizard-settings-150.png "vytvořit DesktopApp v nastavení Průvodce aplikací Win32")

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt DesktopApp, zvolte **přidat**a klikněte na tlačítko **nová položka**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "přidat novou položku do projektu DesktopApp")

1. V **přidat novou položku** dialogu **soubor C++ (.cpp)**. V **název** zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **přidat**.

   ![Soubor .cpp přidat do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "přidat soubor .cpp DesktopApp projektu")

Váš projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru.

## <a name="create-the-code"></a>Vytvoření kódu

V dalším kroku se dozvíte, jak vytvořit kód pro aplikace klasické pracovní plochy Windows v sadě Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Spuštění aplikace klasické pracovní plochy Windows

1. Stejně jako každý C musí mít aplikace a aplikace v C++ `main` fungovat jako výchozí bod, každý Windows musí mít aplikace klasické pracovní plochy `WinMain` funkce. `WinMain` má následující syntaxi.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Informace o parametrech a vrácených hodnotách této funkce najdete v tématu [WinMain vstupní bod](https://msdn.microsoft.com/library/windows/desktop/ms633559).

   > [!NOTE]
   > Co jsou všechny tyto nadbytečná slova, jako je například `CALLBACK`, nebo `HINSTANCE`, nebo `_In_`? Tradiční rozhraní Windows API používá – definice TypeDef a makra preprocesoru pro abstrakci některé podrobnosti typů a specifické pro platformu. kód, jako je například konvence volání, **__declspec** deklarace a pragma kompilátoru. V sadě Visual Studio, můžete použít technologie IntelliSense [rychlé informace](/visualstudio/ide/using-intellisense#quick-info) funkce naleznete v tématu co definování těchto funkcí TypeDef a makra. Umístěte ukazatel myši nad slovo, které vás zajímají, nebo ho vyberte a stiskněte klávesu **Ctrl**+**K**, **Ctrl**+**můžu** pro malého vyskakovacího okna, který obsahuje definici. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense). Parametry a návratové typy často používají *poznámky SAL* umožňují catch programovací chyby. Další informace najdete v tématu [použití anotací SAL k omezení defektů kódu C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Aplikace klasické pracovní plochy Windows vyžadují &lt;windows.h >. &lt;Tchar.h > definuje `TCHAR` makro, které řeší nakonec k **wchar_t** Pokud a symbolů UNICODE je definován ve vašem projektu, jinak se překládá na **char**.  Při sestavování vždy s povoleným kódem UNICODE, není nutné Tchar – a můžete pouze **wchar_t** přímo.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Kromě `WinMain` funkce, každá aplikace klasické pracovní plochy Windows musí mít také funkci procedury okna. Tato funkce se obvykle nazývá `WndProc` , ale název můžete libovolně. `WndProc` má následující syntaxi.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   V této funkci, napište kód pro zpracování *zprávy* , která přijímá aplikace z Windows při *události* dojít. Například pokud uživatel vybere tlačítko OK v aplikaci, Windows odešle zprávu, a můžete napsat kód uvnitř vaší `WndProc` funkce, která provádí práci je vhodné. Je volána *zpracování* událost. Pouze zpracování událostí, které jsou relevantní pro vaši aplikaci.

   Další informace najdete v tématu [procedury okna](https://msdn.microsoft.com/library/windows/desktop/ms632593).

### <a name="to-add-functionality-to-the-winmain-function"></a>Přidání funkčnosti do funkce WinMain

1. V `WinMain` funkce, naplnění strukturu typu [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577). Struktura obsahuje informace o okně, například ikonu aplikace, barvy pozadí okna, název má být zobrazen v záhlaví a co je důležité, ukazatel na funkci procedury okna. Následující příklad ukazuje typickou `WNDCLASSEX` struktury.

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

   Informace o polích struktury výše najdete v tématu [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577).

1. Zaregistrujte `WNDCLASSEX` s Windows tak, že ví o okně aplikace a jak odesílat zprávy do něj. Použití [RegisterClassEx](https://msdn.microsoft.com/library/windows/desktop/ms633587) fungovat a předejte strukturu třídy okna jako argument. `_T` – Makro se používá, protože používáme `TCHAR` typu.

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

1. Nyní můžete vytvořit časové období. Použití [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) funkce.

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

   Tato funkce vrátí `HWND`, což je popisovač okna. Popisovač je něco jako ukazatel, který používá Windows ke sledování otevřená okna. Další informace najdete v tématu [datové typy Windows](/windows/desktop/WinProg/windows-data-types).

1. V tomto okamžiku v okně se vytvořil, ale musíme říct Windows, aby byla viditelná. Je to, čemu tento kód:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Zobrazené okno nemá příliš mnoho obsahu, protože dosud nebyla implementována `WndProc` funkce. Jinými slovy aplikace neošetřuje ještě zprávy, které je teď odesílání Windows.

1. Zpracování zpráv, jsme nejprve přidejte smyčku přijímat zprávy, které odešle Windows. Když aplikace obdrží zprávu, smyčka ji odešle vaše `WndProc` funkci ke zpracování. Smyčky zpráv vypadá podobně jako následující kód.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Další informace o strukturách a funkcích ve smyčce zpráv naleznete v tématu [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958), [GetMessage](https://msdn.microsoft.com/library/windows/desktop/ms644936), [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage), a [DispatchMessage ](/windows/desktop/api/winuser/nf-winuser-dispatchmessage).

   V tomto okamžiku `WinMain` funkce by měla vypadat podobně jako následující kód.

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

### <a name="to-add-functionality-to-the-wndproc-function"></a>Přidání funkčnosti do funkce WndProc

1. Povolit `WndProc` funkce pro zpracování zprávy, které aplikace obdrží, implementovat příkaz switch.

   Je důležité zpráv pro zpracování [WM_PAINT](/windows/desktop/gdi/wm-paint) zprávy. Aplikace obdrží `WM_PAINT` zprávy, když část zobrazeného okna musí být aktualizovány. Události může dojít, když uživatel přesune časové období před okno a poté přesunut ho znovu a vaše aplikace nebude vědět, když dojde k těmto událostem. Pouze Windows ví, takže se zobrazí oznámení s `WM_PAINT`. Při prvním zobrazení okna musí být aktualizovány všechny jeho.

   Pro zpracování `WM_PAINT` zprávy, první volání [BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint), následně zpracovat veškerou logiku pro vykreslení textu, tlačítek a dalších ovládacích prvků v okně a následně zavolat [EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint). Pro aplikace je logika mezi zahajovacím a ukončovacím voláním zobrazí řetězec "Hello, plochu Windows!" v okně. V následujícím kódu, Všimněte si, [TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta) funkce slouží k zobrazení řetězce.

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

   `HDC` v kódu je popisovač kontextu zařízení, což je datová struktura, která používá Windows umožňují aplikaci komunikovat s grafický podsystém. `BeginPaint` a `EndPaint` funkce vaše aplikace chovat jako dobrý občany a nepoužívá kontext zařízení pro delší, než je potřeba. Zpřístupnění nápovědy funkce grafický podsystém je k dispozici pro použití jiné aplikace.

1. Aplikace obvykle zpracovává mnoho jiných zpráv, například [WM_CREATE](/windows/desktop/winmsg/wm-create) při prvním vytvoření okna a [WM_DESTROY](/windows/desktop/winmsg/wm-destroy) při zavření okna. Následující kód ukazuje základní, ale dokončení `WndProc` funkce.

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

## <a name="build-the-code"></a>Sestavení kódu

Jak jsme slíbili, tady je kompletní kód pro funkční aplikaci.

### <a name="to-build-this-example"></a>Sestavení tohoto příkladu

1. Smažete veškerý kód, který jste zadali v *HelloWindowsDesktop.cpp* v editoru. Tento příklad kódu zkopírujte a vložte ho do *HelloWindowsDesktop.cpp*:

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

1. Na **sestavení** nabídce zvolte **sestavit řešení**. Výsledky kompilace, při které by se měla zobrazit v **výstup** okna v sadě Visual Studio.

   ![Sestavit projekt DesktopApp](../build/media/desktop-app-project-build-150.gif "DesktopApp projekt sestavit")

1. Chcete-li aplikaci spustit, stiskněte **F5**. Okno, které obsahuje text "Hello, plochu Windows!" se zobrazí v levém horním rohu zobrazení.

   ![Spusťte projekt DesktopApp](../build/media/desktop-app-project-run-157.png ", spusťte projekt DesktopApp")

Blahopřejeme! Dokončení tohoto návodu a integrované tradiční desktopové aplikace Windows.

## <a name="see-also"></a>Viz také

[Desktopové aplikace Windows](../windows/windows-desktop-applications-cpp.md)