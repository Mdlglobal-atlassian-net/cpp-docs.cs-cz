---
title: 'Návod: Vytvoření tradiční desktopové aplikace pro WindowsC++()'
ms.custom: get-started-article
ms.date: 04/23/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 8bc2a42c5a9006065e2f0f4ecb70911e0055823e
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71062061"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Návod: Vytvoření tradiční desktopové aplikace pro WindowsC++()

Tento návod ukazuje, jak vytvořit tradiční desktopovou aplikaci pro Windows v aplikaci Visual Studio. Ukázková aplikace, kterou vytvoříte, používá rozhraní Windows API k zobrazení "Hello, Windows Desktop!" v okně. Kód, který vyvíjíte v tomto návodu, můžete použít jako vzor pro vytváření dalších aplikací pro stolní počítače se systémem Windows.

Rozhraní API systému Windows (označované také jako Win32 API, rozhraní Windows Desktop API a Windows Classic API) je architektura založená na jazyce C pro vytváření aplikací pro Windows. Vzhledem k tomu, že se 1980s a byl použit k vytváření aplikací pro Windows po dobu dekád, byl už existence. Na rozhraní Windows API, jako je MFC, ATL a rozhraní .NET Framework, byly postaveny pokročilejší a snazší architektury programování. I nejaktuálnější kód pro UWP a aplikace ze Storu napsané v C++/WinRT používá rozhraní API systému Windows pod. Další informace o rozhraní API systému Windows najdete v tématu [index rozhraní API pro Windows](/windows/win32/apiindex/windows-api-list). Existuje mnoho způsobů, jak vytvářet aplikace pro systém Windows, ale výše uvedený postup byl první.

> [!IMPORTANT]
> V zájmu zkrácení jsou v textu vynechány některé příkazy kódu. Část [sestavení kódu](#build-the-code) na konci tohoto dokumentu zobrazuje kompletní kód.

## <a name="prerequisites"></a>Požadavky

- Počítač se systémem Microsoft Windows 7 nebo novější verzí. Pro nejlepší vývojové prostředí doporučujeme Windows 10.

- Kopie sady Visual Studio. Informace o tom, jak stáhnout a nainstalovat Visual Studio, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že je zaškrtnuté políčko **vývoj pro stolní počítače pomocí C++**  úlohy. Nedělejte si starosti, pokud jste při instalaci sady Visual Studio nenainstalovali tuto úlohu. Instalační program můžete spustit znovu a nainstalovat hned.

   ![Vývoj desktopových C++ aplikací pomocí](../build/media/desktop-development-with-cpp.png "Vývoj desktopových C++ aplikací pomocí")

- Porozumění základům používání integrovaného vývojového prostředí (IDE) sady Visual Studio Pokud jste už používali desktopové aplikace pro Windows, můžete si je nechat. Úvod najdete v tématu [prohlídka funkcí rozhraní IDE sady Visual Studio](/visualstudio/ide/visual-studio-ide).

- Seznamte se s dostatečným základem C++ jazyka, který se má sledovat. Nedělejte si starosti, nemůžeme nic složitě.

## <a name="create-a-windows-desktop-project"></a>Vytvořit desktopový projekt pro Windows

Postupujte podle těchto kroků a vytvořte svůj první desktopový projekt pro Windows a zadejte kód pro fungující desktopovou aplikaci pro Windows. Ujistěte se, že selektor verzí v levém horním rohu této stránky je nastaven na správnou verzi sady Visual Studio, kterou používáte.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Vytvoření desktopového projektu Windows v aplikaci Visual Studio 2019

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte na **Desktop**. 

1. Z filtrovaného seznamu typů projektů zvolte možnost **Průvodce desktopovým systémem Windows** a pak zvolte možnost **Další**. Na další stránce zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

1. Zobrazí se dialogové okno **projekt pro stolní počítače se systémem Windows** . V části **Typ aplikace**vyberte **aplikace systému Windows (. exe)** . V části **Další možnosti**vyberte **prázdný projekt**. Kliknutím na **tlačítko OK** vytvořte projekt.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **DesktopApp** , zvolte možnost **Přidat**a pak zvolte možnost **Nová položka**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Přidat novou položku do projektu DesktopApp")

1. V dialogovém okně **Přidat novou položku** vyberte  **C++ soubor (. cpp)** . Do pole **název** zadejte název souboru, například *HelloWindowsDesktop. cpp*. Zvolte **přidat**.

   ![Přidat soubor. cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Přidat soubor. cpp do projektu DesktopApp")

Projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru. Chcete-li pokračovat, přeskočte dopředu a [vytvořte kód](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Vytvoření desktopového projektu Windows v aplikaci Visual Studio 2017

1. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.

1. V dialogovém okně **Nový projekt** rozbalte v levém podokně položku **nainstalovaná** > **C++aplikace Visual**a pak vyberte možnost **desktopová plocha systému Windows**. V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**.

   Do pole **název** zadejte název projektu, například *DesktopApp*. Zvolte **OK**.

   ![Pojmenování projektu DesktopApp](../build/media/desktop-app-new-project-name-153.png "Pojmenování projektu DesktopApp")

1. V dialogovém okně **pracovní projekt Windows** v části **Typ aplikace**vyberte možnost **aplikace systému Windows (. exe)** . V části **Další možnosti**vyberte **prázdný projekt**. Kliknutím na **tlačítko OK** vytvořte projekt.

   ![Průvodce vytvořením DesktopApp v desktopovém projektu Windows](../build/media/desktop-app-new-project-wizard-153.png "Průvodce vytvořením DesktopApp v desktopovém projektu Windows")

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **DesktopApp** , zvolte možnost **Přidat**a pak zvolte možnost **Nová položka**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Přidat novou položku do projektu DesktopApp")

1. V dialogovém okně **Přidat novou položku** vyberte  **C++ soubor (. cpp)** . Do pole **název** zadejte název souboru, například *HelloWindowsDesktop. cpp*. Zvolte **přidat**.

   ![Přidat soubor. cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-153.png "Přidat soubor. cpp do projektu DesktopApp")

Projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru. Chcete-li pokračovat, přeskočte dopředu a [vytvořte kód](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Vytvoření desktopového projektu Windows v aplikaci Visual Studio 2015

1. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.

1. V dialogovém okně **Nový projekt** rozbalte v levém podokně položku **nainstalované** > **šablony** > **vizuál C++** a pak vyberte **Win32**. V prostředním podokně vyberte **projekt Win32**.

   Do pole **název** zadejte název projektu, například *DesktopApp*. Zvolte **OK**.

   ![Pojmenování projektu DesktopApp](../build/media/desktop-app-new-project-name-150.png "Pojmenování projektu DesktopApp")

1. Na stránce **Přehled** v **Průvodci aplikací Win32**klikněte na tlačítko **Další**.

   ![Přehled Průvodce vytvořením DesktopApp v aplikaci Win32](../build/media/desktop-app-win32-wizard-overview-150.png "Přehled Průvodce vytvořením DesktopApp v aplikaci Win32")

1. Na stránce **nastavení aplikace** klikněte v části **Typ aplikace**na položku **aplikace systému Windows**. V části **Další možnosti**vyberte **prázdný projekt**. Kliknutím na tlačítko **Dokončit** vytvořte projekt.

   ![Vytvoření DesktopApp v nastavení Průvodce aplikací Win32](../build/media/desktop-app-win32-wizard-settings-150.png "Vytvoření DesktopApp v nastavení Průvodce aplikací Win32")

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt DesktopApp, zvolte možnost **Přidat**a pak zvolte možnost **Nová položka**.

   ![Přidat novou položku do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Přidat novou položku do projektu DesktopApp")

1. V dialogovém okně **Přidat novou položku** vyberte  **C++ soubor (. cpp)** . Do pole **název** zadejte název souboru, například *HelloWindowsDesktop. cpp*. Zvolte **přidat**.

   ![Přidat soubor. cpp do projektu DesktopApp](../build/media/desktop-app-add-cpp-file-150.png "Přidat soubor. cpp do projektu DesktopApp")

Projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru.

::: moniker-end

## <a name="create-the-code"></a>Vytvoření kódu

V dalším kroku se dozvíte, jak vytvořit kód pro desktopovou aplikaci systému Windows v aplikaci Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Spuštění aplikace klasické pracovní plochy systému Windows

1. Stejně jako každá aplikace a C++ aplikace jazyka C musí mít `main` funkci jako výchozí bod, každá desktopová `WinMain` aplikace systému Windows musí mít funkci. `WinMain`má následující syntaxi.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Informace o parametrech a návratové hodnotě této funkce naleznete v tématu [WinMain Entry Point](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Jaká jsou všechna další slova, například `CALLBACK`, nebo `HINSTANCE` `_In_`nebo? Tradiční rozhraní API systému Windows používá rozsáhly definice typedef a makra preprocesoru pro abstrakci některých podrobností o typech a kódu specifického pro platformu, jako jsou konvence volání, deklarace **__declspec** a direktivy pragma kompilátoru. V aplikaci Visual Studio můžete pomocí funkce [rychlá informace](/visualstudio/ide/using-intellisense#quick-info) technologie IntelliSense zobrazit, co tyto definice typedef a makra definují. Najeďte myší na slovo, které vás zajímá, nebo ho vyberte a stiskněte klávesovou **zkratku CTRL**++**k**, **CTRL**+**I** pro malé automaticky otevírané okno, které obsahuje definici. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense). Parametry a návratové typy často používají *poznámky SAL* , které vám pomůžou zachytit programové chyby. Další informace najdete v tématu [Použití poznámek SAL ke snížení vad CC++ /kódu](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Desktopové programy Windows &lt;vyžadují > Windows. h. &lt;Tchar. h > definuje `TCHAR` makro, které se nakonec překládá na **wchar_t** , pokud je v projektu definován symbol Unicode, v opačném případě se překládá na **char**.  Pokud vždy sestavíte s povoleným kódováním UNICODE, nepotřebujete TCHAR a můžete pouze použít **wchar_t** přímo.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Kromě `WinMain` funkce musí mít každá desktopová aplikace pro Windows také funkci Window-Procedure. Tato funkce se obvykle nazývá `WndProc` , ale můžete ji pojmenovat libovolně. `WndProc`má následující syntaxi.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   V této funkci napíšete kód, který bude zpracovávat *zprávy* , které aplikace obdrží ze systému Windows, když dojde k *události* . Například pokud uživatel klikne na tlačítko OK v aplikaci, Windows vám pošle zprávu a vy budete moct psát kód ve `WndProc` funkci, která funguje podle potřeby. Nazývá se *zpracování* události. Zpracujete pouze události, které jsou relevantní pro vaši aplikaci.

   Další informace naleznete v tématu [procedury okna](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Přidání funkcí do funkce WinMain

1. Ve funkci naplníte strukturu typu [WNDCLASSEX.](/windows/win32/api/winuser/ns-winuser-wndclassexw) `WinMain` Struktura obsahuje informace o okně, například ikonu aplikace, barva pozadí okna, název, který se má zobrazit v záhlaví a důležité, ukazatel na funkci okna. Následující příklad ukazuje typickou `WNDCLASSEX` strukturu.

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

   Informace o polích struktury výše najdete v tématu [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Zaregistrujte se v `WNDCLASSEX` systému Windows, aby ví o vašem okně a bylo možné do něj odesílat zprávy. Použijte funkci [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) a předejte strukturu třídy okna jako argument. Makro se používá, protože `TCHAR` používáme typ. `_T`

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

1. Nyní můžete vytvořit okno. Použijte funkci [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) .

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

   Tato funkce vrací objekt `HWND`, který je popisovačem okna. Popisovač je trochu podobný jako ukazatel, který systém Windows používá ke sledování otevřených oken. Další informace najdete v tématu [datové typy Windows](/windows/win32/WinProg/windows-data-types).

1. V tomto okamžiku bylo okno vytvořeno, ale stále je potřeba sdělit Windows, aby se zobrazilo. To je to, co tento kód dělá:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Zobrazené okno nemá mnohem obsah, protože jste ještě neimplementovali `WndProc` funkci. Jinými slovy aplikace ještě nezpracovává zprávy, na které Windows právě odesílá.

1. Aby bylo možné zprávy zpracovat, nejprve přidáme smyčku zpráv, která bude naslouchat zprávám, které Windows odesílá. Když aplikace obdrží zprávu, tato smyčka ji odešle do `WndProc` funkce, která má být zpracována. Smyčka zpráv se podobá následujícímu kódu.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Další informace o strukturách a funkcích ve smyčce zpráv naleznete v tématu [MSG](/windows/win32/api/winuser/ns-winuser-msg), [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

   V tomto okamžiku `WinMain` by funkce měla vypadat podobně jako následující kód.

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

### <a name="to-add-functionality-to-the-wndproc-function"></a>Přidání funkce do funkce WndProc

1. Chcete-li `WndProc` povolit funkci zpracování zpráv, které aplikace přijímá, implementujte příkaz switch.

   Jednu důležitou zprávu, která se má zpracovat, je zpráva [WM_PAINT](/windows/win32/gdi/wm-paint) . Aplikace obdrží `WM_PAINT` zprávu, je-li část zobrazeného okna aktualizována. K události může dojít, když uživatel přesune okno před okno, potom ho znovu přesune a vaše aplikace neví, kdy k těmto událostem dojde. Pouze systém Windows zná, takže vás na to upozorní `WM_PAINT`. Po prvním zobrazení okna se musí aktualizovat všechny.

   Chcete-li `WM_PAINT` zpracovat zprávu, nejprve zavolejte [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint)a potom zpracujte veškerou logiku pro rozložení textu, tlačítek a dalších ovládacích prvků v okně a pak zavolejte [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). Pro aplikaci logika mezi počátečním voláním a koncovým voláním je zobrazení řetězce "Hello, Windows Desktop!" v okně. V následujícím kódu si všimněte, že funkce [text](/windows/win32/api/wingdi/nf-wingdi-textoutw) je použita k zobrazení řetězce.

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

   `HDC`v kódu je popisovačem kontextu zařízení, což je datová struktura, kterou systém Windows používá k tomu, aby aplikace mohla komunikovat s grafickým subsystémem. Funkce `BeginPaint` a`EndPaint` umožňují, aby se vaše aplikace chovala jako dobrá občan a nepoužívala kontext zařízení po dobu delší, než je potřeba. Funkce pomůžou zajistit, aby byl podsystém grafiky k dispozici pro použití v jiných aplikacích.

1. Aplikace obvykle zpracovává mnoho dalších zpráv, například [WM_CREATE](/windows/win32/winmsg/wm-create) při prvním vytvoření okna a [WM_DESTROY](/windows/win32/winmsg/wm-destroy) při zavření okna. Následující kód ukazuje základní, ale úplnou `WndProc` funkci.

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

Jak jste slíbili, tady je kompletní kód pro funkční aplikaci.

### <a name="to-build-this-example"></a>Sestavení tohoto příkladu

1. Odstraňte veškerý kód, který jste zadali v *HelloWindowsDesktop. cpp* v editoru. Zkopírujte tento ukázkový kód a vložte jej do *HelloWindowsDesktop. cpp*:

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

1. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**. Výsledky kompilace by se měly zobrazit v okně **výstup** v aplikaci Visual Studio.

   ![Sestavení projektu DesktopApp](../build/media/desktop-app-project-build-150.gif "Sestavení projektu DesktopApp")

1. Chcete-li spustit aplikaci, stiskněte klávesu **F5**. Okno, které obsahuje text "Hello, Windows Desktop!" měl by se zobrazit v levém horním rohu zobrazení.

   ![Spuštění projektu DesktopApp](../build/media/desktop-app-project-run-157.PNG "Spuštění projektu DesktopApp")

Blahopřejeme! Dokončili jste tento návod a vytvořili tradiční desktopovou aplikaci pro Windows.

## <a name="see-also"></a>Viz také:

[Desktopové aplikace pro Windows](../windows/windows-desktop-applications-cpp.md)
