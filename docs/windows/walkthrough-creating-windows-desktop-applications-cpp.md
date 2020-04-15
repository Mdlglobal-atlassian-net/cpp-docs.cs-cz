---
title: 'Návod: Vytvoření tradiční aplikace Pro Plochu systému Windows (C++)'
description: Jak vytvořit minimální, tradiční windows desktopové aplikace pomocí Sady Visual Studio, C++ a Win32 API
ms.custom: get-started-article
ms.date: 11/03/2019
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: da74778e79a08dd3ed2b5be0675981425264bdc0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351841"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>Návod: Vytvoření tradiční aplikace Pro Plochu systému Windows (C++)

Tento návod ukazuje, jak vytvořit tradiční desktopovou aplikaci systému Windows v sadě Visual Studio. Ukázková aplikace, kterou vytvoříte, používá rozhraní API systému Windows k zobrazení "Hello, Windows desktop!" v okně. Kód, který vyvíjíte v tomto návodu, můžete použít jako vzorek k vytvoření jiných aplikací pro stolní počítače systému Windows.

Rozhraní API systému Windows (označované také jako rozhraní API Win32, rozhraní API pro stolní počítače windows a rozhraní Windows Classic API) je rozhraní založené na jazyce C pro vytváření aplikací systému Windows. To bylo v existenci od roku 1980 a byl použit k vytváření aplikací systému Windows po celá desetiletí. Pokročilejší a snadněji programované architektury byly postaveny na rozhraní API systému Windows. Například MFC, ATL, rozhraní .NET. Dokonce i nejmodernější kód prostředí Windows Runtime pro aplikace UPW a Store napsaný v jazyce C++/WinRT používá rozhraní API systému Windows pod ním. Další informace o rozhraní API systému Windows naleznete v [tématu Windows API Index](/windows/win32/apiindex/windows-api-list). Existuje mnoho způsobů, jak vytvářet aplikace systému Windows, ale výše uvedený proces byl první.

> [!IMPORTANT]
> Z důvodu stručnosti jsou některé příkazy kódu vynechány v textu. [Sestavení kódu](#build-the-code) části na konci tohoto dokumentu zobrazuje úplný kód.

## <a name="prerequisites"></a>Požadavky

- Počítač se systémem Microsoft Windows 7 nebo novějšími verzemi. Doporučujeme Windows 10 pro nejlepší vývojové prostředí.

- Kopie sady Visual Studio. Informace o stažení a instalaci sady Visual Studio naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Při spuštění instalačního programu zkontrolujte, zda je kontrolován vývoj plochy s úlohami **jazyka C++.** Nebojte se, pokud jste nenainstalovali tuto úlohu při instalaci Sady Visual Studio. Instalační program můžete spustit znovu a nainstalovat jej nyní.

   ![Vývoj plochy s C++](../build/media/desktop-development-with-cpp.png "Vývoj desktopových aplikací pomocí C++")

- Pochopení základy použití ide sady Visual Studio. Pokud jste aplikace klasické pracovní plochy pro Windows používali už dříve, můžete pravděpodobně držet krok. Úvod najdete v tématu [Visual Studio IDE prohlídka funkce](/visualstudio/ide/visual-studio-ide).

- Pochopení dostatek základů jazyka C++ sledovat. Nebojte se, neděláme nic moc komplikovaného.

## <a name="create-a-windows-desktop-project"></a>Vytvoření projektu plochy Windows

Podle těchto kroků vytvořte svůj první projekt plochy systému Windows. Jak budete pokračovat, zadáte kód pro pracovní desktopovou aplikaci windows. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2019"></a>Vytvoření projektu plochy Windows v Sadě Visual Studio 2019

1. V hlavní nabídce zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Windows**a typ **projektu** na **plochu**.

1. Z filtrovaného seznamu typů projektů zvolte **Průvodce plochu systému Windows** a pak zvolte **Další**. Na další stránce zadejte název projektu, například *DesktopApp*.

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

1. Nyní se zobrazí dialogové okno **Projekt plochy systému Windows.** V části **Typ aplikace**vyberte **Možnost Desktopová aplikace (.exe)**. V části **Další možnosti**vyberte **Možnost Prázdný projekt**. Chcete-li vytvořit projekt, zvolte **OK.**

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt **DesktopApp,** zvolte **Přidat**a pak zvolte **Nová položka**.

   ![Přidání nové položky do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Přidání nové položky do projektu DesktopApp")

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**. Do pole **Název** zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **Přidat**.

   ![Přidání souboru CPP do aplikace DesktopApp Project](../build/media/desktop-app-add-cpp-file-153.png "Přidání souboru CPP do aplikace DesktopApp Project")

Projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru. Chcete-li pokračovat, přeskočte dopředu na [vytvoření kódu](#create-the-code).

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017"></a>Vytvoření projektu plochy Windows ve Visual Studiu 2017

1. V nabídce **Soubor** zvolte **Nový** a pak zvolte **Project**.

1. V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Nainstalovaný** > **visual c++** a vyberte **možnost Plocha systému Windows**. V prostředním podokně vyberte **Průvodce plochu systému Windows**.

   Do pole **Název** zadejte název projektu, například *DesktopApp*. Vyberte **OK**.

   ![Pojmenování projektu DesktopApp](../build/media/desktop-app-new-project-name-153.png "Pojmenování projektu DesktopApp")

1. V dialogovém okně **Projekt plochy systému Windows** vyberte v části Typ **aplikace** **aplikaci systému Windows (.exe)**. V části **Další možnosti**vyberte **Možnost Prázdný projekt**. Ujistěte se, že není vybraná možnost **Předkompilované záhlaví.** Chcete-li vytvořit projekt, zvolte **OK.**

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt **DesktopApp,** zvolte **Přidat**a pak zvolte **Nová položka**.

   ![Přidání nové položky do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-153.gif "Přidání nové položky do projektu DesktopApp")

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**. Do pole **Název** zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **Přidat**.

   ![Přidání souboru CPP do aplikace DesktopApp Project](../build/media/desktop-app-add-cpp-file-153.png "Přidání souboru CPP do aplikace DesktopApp Project")

Projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru. Chcete-li pokračovat, přeskočte dopředu na [vytvoření kódu](#create-the-code).

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2015"></a>Vytvoření projektu plochy Windows ve Visual Studiu 2015

1. V nabídce **Soubor** zvolte **Nový** a pak zvolte **Project**.

1. V dialogovém okně **Nový projekt** rozbalte v levém podokně**položku** >  **Nainstalované** > šablony**Visual C++** a vyberte **win32**. V prostředním podokně vyberte **Projekt Win32**.

   Do pole **Název** zadejte název projektu, například *DesktopApp*. Vyberte **OK**.

   ![Pojmenování projektu DesktopApp](../build/media/desktop-app-new-project-name-150.png "Pojmenování projektu DesktopApp")

1. Na stránce **Přehled** **Průvodce aplikací win32**zvolte **Další**.

   ![Vytvořit DesktopApp v Průvodci aplikací Win32 Přehled](../build/media/desktop-app-win32-wizard-overview-150.png "Vytvořit DesktopApp v Průvodci aplikací Win32 Přehled")

1. Na stránce **Nastavení aplikace** vyberte v části **Typ aplikace** **aplikaci systému Windows**. V části **Další možnosti**zrušte **zaškrtnutí políčka Předkompilované záhlaví**a vyberte **možnost Vyprázdnit projekt**. Chcete-li vytvořit projekt, zvolte **Dokončit.**

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt DesktopApp, zvolte **Přidat**a pak zvolte **Nová položka**.

   ![Přidání nové položky do projektu DesktopApp](../build/media/desktop-app-project-add-new-item-150.gif "Přidání nové položky do projektu DesktopApp")

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**. Do pole **Název** zadejte název souboru, například *HelloWindowsDesktop.cpp*. Zvolte **Přidat**.

   ![Přidání souboru CPP do aplikace DesktopApp Project](../build/media/desktop-app-add-cpp-file-150.png "Přidání souboru CPP do aplikace DesktopApp Project")

Projekt je nyní vytvořen a zdrojový soubor je otevřen v editoru.

::: moniker-end

## <a name="create-the-code"></a>Vytvoření kódu

Dále se dozvíte, jak vytvořit kód pro desktopovou aplikaci pro Windows v sadě Visual Studio.

### <a name="to-start-a-windows-desktop-application"></a>Spuštění desktopové aplikace systému Windows

1. Stejně jako každá aplikace jazyka C `main` a aplikace jazyka C++ musí mít `WinMain` funkci jako výchozí bod, musí mít každá desktopová aplikace systému Windows funkci. `WinMain`má následující syntaxi.

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_opt_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   Informace o parametrech a návratové hodnotě této funkce naleznete v tématu [Vstupní bod WinMain](/windows/win32/api/winbase/nf-winbase-winmain).

   > [!NOTE]
   > Jaké jsou všechny ty extra `CALLBACK`slova, jako je , nebo `HINSTANCE`, nebo `_In_`? Tradiční rozhraní API systému Windows používá typedefs a preprocesorm makra značně abstraktní pryč některé podrobnosti typů a kódu specifické pro platformu, jako jsou konvence volání, **__declspec** deklarace a kompilátor pragmas. V sadě Visual Studio můžete pomocí funkce IntelliSense [Quick Info](/visualstudio/ide/using-intellisense#quick-info) zjistit, co tyto typedefs a makra definují. Najeďte myší na slovo zájmu, nebo jej vyberte a stiskněte **Ctrl**+**K**, **Ctrl**+**I** pro malé vyskakovací okno, které obsahuje definici. Další informace naleznete [v tématu Using IntelliSense](/visualstudio/ide/using-intellisense). Parametry a návratové typy často používají *poznámky SAL,* které vám pomohou zachytit chyby programování. Další informace naleznete [v tématu Použití sal poznámky ke snížení C/C++ chybkódu](/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).

1. Desktopové programy &lt;windows vyžadují> windows.h. &lt;tchar.h> definuje `TCHAR` makro, které se nakonec rozhodne **wchar_t** pokud je v projektu definován symbol UNICODE, jinak se překládá na **char**.  Pokud vždy sestavujete s povoleným UNICODE, nepotřebujete TCHAR a můžete použít **pouze wchar_t** přímo.

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. Spolu s `WinMain` funkcí musí mít každá desktopová aplikace systému Windows také funkci procedury okna. Tato funkce je `WndProc`obvykle pojmenována , ale můžete ji pojmenovat, jak se vám líbí. `WndProc`má následující syntaxi.

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hWnd,
      _In_ UINT   message,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   V této funkci napíšete kód pro zpracování *zpráv,* které aplikace obdrží ze systému Windows, když dojde k *událostem.* Pokud například uživatel ve vaší aplikaci zvolí tlačítko OK, systém Windows vám pošle `WndProc` zprávu a můžete do své funkce napsat kód, který provede jakoukoli vhodnou práci. Říká se tomu *vyřizování* události. Zpracováváte pouze události, které jsou relevantní pro vaši aplikaci.

   Další informace naleznete [v tématu Procedury okna](/windows/win32/winmsg/window-procedures).

### <a name="to-add-functionality-to-the-winmain-function"></a>Přidání funkcí do funkce WinMain

1. Ve `WinMain` funkci naplníte strukturu typu [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw). Struktura obsahuje informace o okně: ikona aplikace, barva pozadí okna, název, který se má zobrazit v záhlaví, mimo jiné. Důležité je, že obsahuje ukazatel funkce na proceduru okna. Následující příklad ukazuje `WNDCLASSEX` typickou strukturu.

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

   Informace o polích výše uvedené struktury naleznete v tématu [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw).

1. Zaregistrujte `WNDCLASSEX` systém Windows, aby věděl o vašem okně a o tom, jak do něj odesílat zprávy. Použijte funkci [RegisterClassEx](/windows/win32/api/winuser/nf-winuser-registerclassexw) a předajte jako argument strukturu třídy okna. Makro `_T` se používá, protože `TCHAR` používáme typ.

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

1. Nyní můžete vytvořit okno. Použijte [funkci CreateWindow.](/windows/win32/api/winuser/nf-winuser-createwindoww)

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

   Tato funkce `HWND`vrátí , což je popisovač okna. Popisovač je poněkud podobný ukazatel, který systém Windows používá ke sledování otevřených oken. Další informace naleznete v tématu [Datové typy systému Windows](/windows/win32/WinProg/windows-data-types).

1. V tomto okamžiku bylo okno vytvořeno, ale stále potřebujeme sdělit systému Windows, aby byl viditelný. To je to, co tento kód dělá:

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   Zobrazené okno nemá mnoho obsahu, protože jste ještě `WndProc` neimplementovali funkci. Jinými slovy, aplikace ještě nezpracovává zprávy, které jí systém Windows nyní odesílá.

1. Chcete-li zpracovat zprávy, nejprve přidáme smyčku zpráv, abychom naslouchali zprávám, které systém Windows odesílá. Když aplikace obdrží zprávu, tato smyčka odešle `WndProc` do funkce, která má být zpracována. Smyčka zpráv se podobá následujícímu kódu.

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   Další informace o strukturách a funkcích ve smyčce zpráv naleznete v tématech [MSG](/windows/win32/api/winuser/ns-winuser-msg), [GetMessage](/windows/win32/api/winuser/nf-winuser-getmessage), [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

   V tomto okamžiku `WinMain` by se funkce měla podobat následujícímu kódu.

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

### <a name="to-add-functionality-to-the-wndproc-function"></a>Přidání funkcí do funkce WndProc

1. Chcete-li `WndProc` povolit funkci pro zpracování zpráv, které aplikace obdrží, implementujte příkaz switch.

   Jednou z důležitých zpráv, které je třeba zpracovat, je [zpráva WM_PAINT.](/windows/win32/gdi/wm-paint) Aplikace obdrží zprávu, `WM_PAINT` když musí být aktualizována část zobrazeného okna. K události může dojít, když uživatel přesune okno před okno a potom jej znovu přesune. Vaše aplikace neví, kdy k těmto událostem dojde. Ví to jenom Windows, takže `WM_PAINT` upozorní vaši aplikaci zprávou. Při prvním zobrazení okna musí být aktualizováno vše.

   Chcete-li `WM_PAINT` zpracovat zprávu, nejprve zavolejte [BeginPaint](/windows/win32/api/winuser/nf-winuser-beginpaint), pak zpracovat všechny logiky rozložení textu, tlačítek a dalších ovládacích prvků v okně a potom volání [EndPaint](/windows/win32/api/winuser/nf-winuser-endpaint). Pro aplikaci je logikou mezi počátečním a koncovým voláním zobrazení řetězce "Hello, Windows desktop!" v okně. V následujícím kódu si všimněte, že [textout](/windows/win32/api/wingdi/nf-wingdi-textoutw) funkce se používá k zobrazení řetězce.

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

   `HDC`v kódu je popisovač kontextu zařízení, což je datová struktura, kterou systém Windows používá k tomu, aby aplikace mohla komunikovat s grafickým subsystémem. Funkce `BeginPaint` `EndPaint` a vaše aplikace se chovají jako dobrý občan a nepoužívá kontext zařízení déle, než je potřeba. Funkce pomáhají zpřístupnit grafický podsystém pro použití jinými aplikacemi.

1. Aplikace obvykle zpracovává mnoho dalších zpráv. Například [WM_CREATE](/windows/win32/winmsg/wm-create) při prvním vytvoření okna a [WM_DESTROY](/windows/win32/winmsg/wm-destroy) při zavření okna. Následující kód ukazuje základní, `WndProc` ale úplnou funkci.

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

Jak jsem slíbil, tady je kompletní kód pro pracovní aplikace.

### <a name="to-build-this-example"></a>Chcete-li vytvořit tento příklad

1. Odstraňte veškerý kód, který jste zadali v *hellowindowsdesktop.cpp* v editoru. Zkopírujte tento ukázkový kód a vložte jej do *souboru HelloWindowsDesktop.cpp*:

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
      _In_opt_ HINSTANCE hPrevInstance,
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

1. V nabídce **Build** zvolte **Build Solution**. Výsledky kompilace by se měly objevit v okně **Výstup** v sadě Visual Studio.

   ![Sestavení projektu DesktopApp](../build/media/desktop-app-project-build-150.gif "Sestavení projektu DesktopApp")

1. Chcete-li aplikaci spustit, stiskněte **klávesu F5**. Okno, které obsahuje text "Hello, Windows desktop!" v levém horním rohu displeje.

   ![Spuštění projektu DesktopApp](../build/media/desktop-app-project-run-157.PNG "Spuštění projektu DesktopApp")

Blahopřejeme! Dokončili jste tento návod a vytvořili tradiční desktopovou aplikaci windows.

## <a name="see-also"></a>Viz také

[Aplikace klasické pracovní plochy systému Windows](../windows/windows-desktop-applications-cpp.md)
