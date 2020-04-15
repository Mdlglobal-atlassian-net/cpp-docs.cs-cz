---
title: 'Průvodce přenosem: Spy++'
ms.date: 10/23/2019
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
ms.openlocfilehash: edccf18c3fbc4d6eeec2ed0aa59df0e7d1f85335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353373"
---
# <a name="porting-guide-spy"></a>Průvodce přenosem: Spy++

Tato případová studie přenosu je navržena tak, aby vám poskytla představu o tom, jaký je typický projekt přenosu, typy problémů, se kterými se můžete setkat, a několik obecných tipů a triků pro řešení problémů s přenosem. Není určen jako definitivní průvodce portováním, protože zkušenosti s přenosem projektu do značné míry závisí na specifikách kódu.

## <a name="spy"></a>Spy++

Spy ++ je široce používaný GUI diagnostický nástroj pro plochu systému Windows, který poskytuje všechny druhy informací o prvky uživatelského rozhraní na ploše systému Windows. Zobrazuje úplnou hierarchii oken a poskytuje přístup k metadatům o každém okně a ovládacím prvku. Tato užitečná aplikace je dodávána s Visual Studio po mnoho let. Našli jsme jeho starou verzi, která byla naposledy zkompilována ve Visual C++ 6.0 a portována do Visual Studia 2015. Prostředí pro Visual Studio 2017 nebo Visual Studio 2019 by mělo být téměř identické.

Tento případ jsme považovali za typický pro portování aplikací pro stolní počítače systému Windows, které používají knihovnu MFC a rozhraní API Win32, zejména pro staré projekty, které nebyly aktualizovány s každou verzí visual c++ od visual c++ 6.0.

## <a name="step-1-converting-the-project-file"></a><a name="convert_project_file"></a>Krok 1. Převod souboru projektu.

Soubor projektu, dva staré soubory DSW z visual c++ 6.0, snadno převedeny bez problémů, které vyžadují další pozornost. Jedním z projektů je aplikace Spy++. Druhý je SpyHk, napsaný v C, podpůrná DLL. Složitější projekty nemusí upgradovat tak snadno, jak je popsáno [zde](../porting/visual-cpp-porting-and-upgrading-guide.md).

Po upgradu dvou projektů naše řešení vypadalo takto:

![Spy&#43;&#43; řešení](../porting/media/spyxxsolution.PNG "Spy&#43;&#43; řešení")

Máme dva projekty, jeden s velkým počtem souborů C++ a další DLL, který je napsán v Jazyce C.

## <a name="step-2-header-file-problems"></a><a name="header_file_problems"></a>Krok 2. Problémy se souborem záhlaví

Při vytváření nově převedeného projektu, jedna z prvních věcí, které budete často najít, je, že soubory hlaviček, které váš projekt používá, nejsou nalezeny.

Jeden ze souborů, které nebyly nalezeny v Spy ++ byl verstamp.h. Z internetového vyhledávání jsme zjistili, že pochází z DAO SDK, zastaralé datové technologie. Chtěli jsme zjistit, jaké symboly byly použity z tohoto souboru záhlaví, abychom zjistili, zda je tento soubor opravdu potřebný nebo zda byly tyto symboly definovány jinde, a proto jsme zakomentovali deklaraci souboru záhlaví a znovu zkompilovali. Ukazuje se, že je potřeba jen jeden symbol, VER_FILEFLAGSMASK.

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

Nejjednodušší způsob, jak najít symbol v dostupných souborech zahrnutí, je použít **funkce Najít v souborech** **(Ctrl**+**Shift**+**F)** a určit **adresáře včetně jazyka Visual C++**. Našli jsme to v ntverp.h. Nahradili jsme verstamp.h include s ntverp.h a tato chyba zmizela.

## <a name="step-3-linker-outputfile-setting"></a><a name="linker_output_settings"></a>Krok 3. Nastavení výstupního souboru linkeru

Starší projekty mají někdy soubory umístěné v nekonvenčních umístěních, které mohou způsobit problémy po upgradu. V takovém případě musíme `$(SolutionDir)` přidat do **zahrnout** cestu ve vlastnostech projektu zajistit, že Visual Studio můžete najít některé soubory hlaviček, které jsou umístěny tam, nikoli v jedné ze složek projektu.

MSBuild si stěžuje, že **Vlastnost Link.OutputFile** neodpovídá **targetpath** a **TargetName** hodnoty, vydávání MSB8012.

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link.OutputFile** je výstup sestavení (exe, DLL, například) a `$(TargetDir)$(TargetName)$(TargetExt)`je obvykle konstruován z , dává cestu, název souboru a příponu. Toto je běžná chyba při migraci projektů ze starého nástroje pro sestavení Visual C++ (vcbuild.exe) do nového nástroje sestavení (MSBuild.exe). Vzhledem k tomu, že došlo ke změně nástroje sestavení v sadě Visual Studio 2010, může dojít k tomuto problému při každé migraci projektu před 2010 na 2010 nebo novější verzi. Základním problémem je, že průvodce migrací projektu neaktualizuje hodnotu **Link.OutputFile,** protože není vždy možné určit, jaká hodnota by měla být založena na jiných nastaveních projektu. Proto je obvykle nutné nastavit ručně. Další podrobnosti najdete v tomto [příspěvku](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) na blogu Visual C++.

V tomto případě byla vlastnost **Link.OutputFile** v převedeném projektu nastavena na .\Debug\Spyxx.exe a .\Release\Spyxx.exe pro projekt Spy++ v závislosti na konfiguraci. Nejlepší je jednoduše nahradit tyto pevně zakódované hodnoty `$(TargetDir)$(TargetName)$(TargetExt)` pro všechny **konfigurace**. Pokud to nepomůže, můžete přizpůsobit odtud nebo změnit vlastnosti v části **Obecné,** kde jsou tyto hodnoty nastaveny (vlastnosti jsou **Výstupní adresář**, **Cílový název**a Cílové **rozšíření**. Nezapomeňte, že pokud vlastnost, kterou si prohlížíte, používá makra, můžete v rozevíracím seznamu zvolit **Upravit** a zobrazit dialogové okno, které zobrazuje konečný řetězec s provedenými nahrazeními maker. Všechna dostupná makra a jejich aktuální hodnoty můžete zobrazit výběrem tlačítka **Makra.**

## <a name="step-4-updating-the-target-windows-version"></a><a name="updating_winver"></a>Krok 4. Aktualizace cílové verze systému Windows

Další chyba označuje, že verze WINVER již není podporována v knihovně MFC. WINVER pro Windows XP je 0x0501.

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

Systém Windows XP již není podporován společností Microsoft, takže i když je cílení v sadě Visual Studio povoleno, měli byste v aplikacích uzařovat podporu a povzbuzovat uživatele k přijetí nových verzí systému Windows.

Chcete-li chybu zbavit, definujte hodnotu WINVER aktualizací nastavení **Vlastnosti projektu** na nejnižší verzi systému Windows, na kterou chcete aktuálně cílit. Zde naleznete tabulku hodnot pro různé verze [systému](/windows/win32/WinProg/using-the-windows-headers)Windows .

Soubor *stdafx.h* obsahoval některé z těchto definic maker.

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

WINVER budeme nastavena na Windows 7. Je snazší přečíst kód později, pokud použijete makro pro Windows 7 (_WIN32_WINNT_WIN7), spíše než samotná hodnota (0x0601).

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

## <a name="step-5-linker-errors"></a><a name="linker_errors"></a>Krok 5. Chyby propojovacího nebo jiného než

S těmito změnami SpyHk (DLL) projekt vytvoří, ale vytvoří chybu propojovacího programu.

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

Vstupní bod pro dll by neměl být exportován. Vstupní bod je určen pouze pro volání zavaděče při prvním načtení dll do paměti, takže by neměl být v tabulce exportu, což je pro ostatní volající. Musíme se jen ujistit, že k ní není připojena směrnice **__declspec(dllexport).** V spyxxhk.c, musíme odstranit ze dvou míst, `DLLEntryPoint`prohlášení a definice . Nikdy smysl použít tuto směrnici, ale předchozí verze propojovacího programu a kompilátoru není příznakem jako problém. Novější verze propojovacího programu poskytují upozornění.

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

C DLL projekt, SpyHK.dll, nyní staví a odkazy bez chyb.

## <a name="step-6-more-outdated-header-files"></a><a name="outdated_header_files"></a>Krok 6. Další zastaralé soubory hlaviček

V tomto bodě začneme pracovat na hlavním spustitelném projektu, Spyxx.

Několik dalších zahrnutých souborů nebylo nalezeno: ctl3d.h a penwin.h. I když může být užitečné prohledat internet a pokusit se zjistit, co obsahuje záhlaví, někdy informace nejsou tak užitečné. Zjistili jsme, že soubor ctl3d.h byl součástí sady Exchange Development Kit a poskytoval podporu pro určitý styl ovládacích prvků v systému Windows 95 a soubor penwin.h se vztahuje k aplikaci Window Pen Computing, zastaralému rozhraní API. V tomto případě jednoduše zakomentujeme `#include` řádek a zabýváme se nedefinovanými symboly, jako jsme to udělali s verstamp.h. Vše, co se týká 3D ovládacích prvků nebo Pen Computing byl odstraněn z projektu.

Vzhledem k tomu, projekt s mnoha chybkompilace, které jsou postupně eliminovat, není reálné najít všechny `#include` použití zastaralé rozhraní API hned při odebrání směrnice. Nezjistili jsme to okamžitě, ale spíše v určitém pozdějším okamžiku došlo k chybě, že WM_DLGBORDER nebyla definována. Je to vlastně jen jeden mnoho nedefinovaných symbolů, které pocházejí z ctl3d.h. Jakmile zjistíme, že se vztahuje k zastaralé rozhraní API, jsme odebrali všechny odkazy v kódu k němu.

## <a name="step-7-updating-old-iostreams-code"></a><a name="updating_iostreams_code"></a>Krok 7. Aktualizace starého kódu iostreams

Další chyba je společná u starého kódu C++, který používá iostreams.

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

Problém je, že stará knihovna iostreams byla odebrána a nahrazena. Musíme nahradit staré iostreamy novějšími standardy.

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

Jedná se o aktualizované zahrnuje:

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

S touto změnou máme `ostrstream`problémy s , který se již nepoužívá. Příslušná náhrada je ostringstream. Snažíme se přidat `ostrstream` **typedef** pro, aby se zabránilo úpravám kódu příliš mnoho, alespoň jako začátek.

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

V současné době je projekt vytvořen pomocí MBCS (Multi-byte Character Set), takže **char** je příslušný znak datový typ. Chcete-li však povolit snadnější aktualizaci kódu na Unicode `TCHAR`UTF-16, aktualizujeme jej na , který se překládá na **char** nebo **wchar_t** v závislosti na tom, zda je vlastnost **Znaková sada** v nastavení projektu nastavena na MBCS nebo Unicode.

Několik dalších částí kódu je třeba aktualizovat.  Základní třídu `ios` jsme `ios_base`nahradili a ostream jsme\<nahradili basic_ostream T>. Přidáme dva další typedefs a tato část zkompiluje.

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

Použití těchto typedefs je pouze dočasné řešení. Pro trvalejší řešení můžeme aktualizovat každý odkaz na přejmenované nebo zastaralé rozhraní API.

Tady je další chyba.

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

Dalším problémem `basic_stringbuf` je, že `freeze` nemá metodu. Metoda `freeze` se používá k zabránění nevracení paměti ve staré `ostream`. Nepotřebujeme to teď, když používáme nové `ostringstream`. Můžeme odstranit volání `freeze`.

```cpp
//rdbuf()->freeze(0);
```

Další dvě chyby došlo na sousedních řádcích. První si stěžuje `ends`na použití , `iostream` což je vi manipulátor staré knihovny, který přidá zakončení null do řetězce. Druhá z těchto chyb vysvětluje, že `str` výstup metody nelze přiřadit k ukazateli bez const.

```cpp
// Null terminate the string in the buffer and
// get a pointer to it.
//
*this << ends;
LPSTR psz = str();
```

```Output
2>mstream.cpp(167): error C2065: 'ends': undeclared identifier2>mstream.cpp(168): error C2440: 'initializing': cannot convert from 'std::basic_string<char,std::char_traits<char>,std::allocator<char>>' to 'LPSTR'
```

Použití nové knihovny `ends` datového proudu není potřeba, protože řetězec je vždy ukončen a nula, takže řádek lze odebrat. Pro druhý problém je problém, `str()` že nyní nevrátí ukazatel na pole znaků pro řetězec; vrátí `std::string` typ. Řešení druhé je změnit typ `LPCSTR` a použít `c_str()` metodu k vyžádání ukazatele.

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

V tomto kódu došlo k chybě, která nás na chvíli zmátla.

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

MOUT makra `*g_pmout` řeší, na které `mstream`je objekt typu . Třída `mstream` je odvozena od třídy `std::basic_ostream<TCHAR>`standardního výstupního řetězce . Nicméně \_s T kolem literálu řetězce, který jsme vložili do přípravy na převod na Unicode, rozlišení přetížení pro **operátor <<** selže s následující chybovou zprávou:

```Output
1>winmsgs.cpp(4612): error C2666: 'mstream::operator <<': 2 overloads have similar conversions
1>  c:\source\spyxx\spyxx\mstream.h(120): note: could be 'mstream &mstream::operator <<(ios &(__cdecl *)(ios &))'
1>  c:\source\spyxx\spyxx\mstream.h(118): note: or       'mstream &mstream::operator <<(ostream &(__cdecl *)(ostream &))'
1>  c:\source\spyxx\spyxx\mstream.h(116): note: or       'mstream &mstream::operator <<(ostrstream &(__cdecl *)(ostrstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(114): note: or       'mstream &mstream::operator <<(mstream &(__cdecl *)(mstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(109): note: or       'mstream &mstream::operator <<(LPTSTR)'
1>  c:\source\spyxx\spyxx\mstream.h(104): note: or       'mstream &mstream::operator <<(TCHAR)'
1>  c:\source\spyxx\spyxx\mstream.h(102): note: or       'mstream &mstream::operator <<(DWORD)'
1>  c:\source\spyxx\spyxx\mstream.h(101): note: or       'mstream &mstream::operator <<(WORD)'
1>  c:\source\spyxx\spyxx\mstream.h(100): note: or       'mstream &mstream::operator <<(BYTE)'
1>  c:\source\spyxx\spyxx\mstream.h(95): note: or       'mstream &mstream::operator <<(long)'
1>  c:\source\spyxx\spyxx\mstream.h(90): note: or       'mstream &mstream::operator <<(unsigned int)'
1>  c:\source\spyxx\spyxx\mstream.h(85): note: or       'mstream &mstream::operator <<(int)'
1>  c:\source\spyxx\spyxx\mstream.h(83): note: or       'mstream &mstream::operator <<(HWND)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1132): note: or       'CDumpContext &operator <<(CDumpContext &,COleSafeArray &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1044): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1042): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1037): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1035): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1030): note: or       'CArchive &operator <<(CArchive &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1028): note: or       'CDumpContext &operator <<(CDumpContext &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(955): note: or       'CArchive &operator <<(CArchive &,ATL::CComBSTR)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(951): note: or       'CArchive &operator <<(CArchive &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(949): note: or       'CDumpContext &operator <<(CDumpContext &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(248): note: or       'CArchive &operator <<(CArchive &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(247): note: or       'CArchive &operator <<(CArchive &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(246): note: or       'CArchive &operator <<(CArchive &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(242): note: or       'CDumpContext &operator <<(CDumpContext &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(241): note: or       'CDumpContext &operator <<(CDumpContext &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(240): note: or       'CDumpContext &operator <<(CDumpContext &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1639): note: or       'CArchive &operator <<(CArchive &,const CObject *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1425): note: or       'CArchive &operator <<(CArchive &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1423): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1418): note: or       'CArchive &operator <<(CArchive &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1416): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(694): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const char *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(741): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(866): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const _Elem *)'
1>          with
1>          [
1>              _Elem=wchar_t
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(983): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>,wchar_t[10]>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &&,const _Ty (&))'
1>          with
1>          [
1>              _Ty=wchar_t [10]
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(1021): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const std::error_code &)'
1>  winmsgs.cpp(4612): note: while trying to match the argument list '(CMsgStream, const wchar_t [10])'
```

Existuje tolik **operátor <<** definice, že tento druh chyby může být zastrašující. Po bližším pohledu na dostupné přetížení, vidíme, že většina z nich `mstream` jsou irelevantní, a při bližším pohledu na definici třídy, jsme identifikovali následující funkce, které si myslíme, že by měly být volány v tomto případě.

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

Důvod, proč není volána, je, že `const wchar_t[10]` literál řetězce má typ, jak můžete vidět z posledního řádku této dlouhé chybové zprávy, takže převod na ukazatel bez const není automatický. Tento operátor by však neměl měnit vstupní parametr, `LPCTSTR` `const char*` takže vhodnější typ parametru je `const wchar_t*` (při kompilaci`char*` jako MBCS a jako `wchar_t*` Unicode), ne `LPTSTR` (při kompilaci jako MBCS a jako Unicode). Provedení této změny opravuje tuto chybu.

Tento typ převodu byl povolen pod starší, méně přísné kompilátoru, ale novější změny shody vyžadují více správný kód.

## <a name="step-8-the-compilers-more-strict-conversions"></a><a name="stricter_conversions"></a>Krok 8. Přísnější převody kompilátoru

Máme také mnoho chyb, jako je následující:

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

K chybě dochází v mapě zpráv, která je jednoduše makro:

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

Chystáte se na definici tohoto makra, vidíme, že odkazuje na funkci `OnNcHitTest`.

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

Problém má co do činění s neshodou v ukazatel na typy členských funkcí. Problém není převod z `CHotLinkCtrl` jako typ třídy `CWnd` jako typ třídy, protože to je platný převod odvozené na základ. Problém je návratový typ: UINT vs LRESULT. LRESULT řeší LONG_PTR což je 64bitový ukazatel nebo 32bitový ukazatel, v závislosti na cílovém binárním typu, takže UINT se nepřevede na tento typ. To není neobvyklé při upgradu kódu napsaného před rokem 2005 od návratový typ mnoha metod mapy zpráv změnil z UINT na LRESULT v sadě Visual Studio 2005 jako součást 64bitové změny kompatibility. Změníme návratový typ z UINT v následujícím kódu na LRESULT:

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

Po změně máme následující kód:

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

Vzhledem k tomu, že existuje asi deset výskytů této funkce v různých třídách odvozených z CWnd, je užitečné použít **Go to Definition** (Klávesnice: **F12)** a **Přejít na deklaraci** (Klávesnice: **Ctrl**+**F12),** když je kurzor na funkci v editoru, abyste je našli a přešli na ně z okna nástroje **Najít symbol.** **Přejít na definici** je obvykle užitečnější z těchto dvou. **Přejít na deklarace** najde deklarace jiné než definující deklarace třídy, jako je například deklarace třídy friend nebo odkazy dopředu.

## <a name="step-9-mfc-changes"></a><a name="mfc_changes"></a>Krok 9. Změny knihovny MFC

Další chyba se také týká změněného typu deklarace a také se vyskytuje v makru.

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

Problém je, že druhý `CWnd::OnActivateApp` parametr změnil z HTASK na DWORD. K této změně došlo v roce 2002 vydání sady Visual Studio, Visual Studio .NET.

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

Musíme aktualizovat deklarace OnActivateApp v odvozených třídách takto:

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

V tomto okamžiku jsme schopni zkompilovat projekt. Existuje však několik upozornění, která je třeba provést, a existují volitelné části upgradu, jako je například převod z mbcs na unicode nebo zlepšení zabezpečení pomocí funkcí Secure CRT.

## <a name="step-10-addressing-compiler-warnings"></a><a name="compiler_warnings"></a>Krok 10. Adresování upozornění kompilátoru

Chcete-li získat úplný seznam upozornění, měli byste provést **znovu sestavit vše** na řešení, nikoli běžné sestavení, jen aby se ujistil, že vše, co dříve zkompilované bude znovu zkompilován, protože dostanete pouze zprávy upozornění z aktuální kompilace. Další otázkou je, zda přijmout aktuální úroveň upozornění nebo použít vyšší úroveň upozornění.  Při přenosu velké množství kódu, zejména starý kód, pomocí vyšší úroveň upozornění může být vhodné.  Můžete také začít s výchozí úroveň upozornění a potom zvýšit úroveň upozornění získat všechna upozornění. Pokud používáte `/Wall`, dostanete několik upozornění v souborech `/W4` záhlaví systému, takže mnoho lidí používá získat nejvíce upozornění na jejich kód bez získání upozornění pro systémové hlavičky. Pokud chcete, aby se upozornění zobrazovala jako chyby, přidejte `/WX` tuto možnost. Tato nastavení jsou v části **C/C++** v dialogovém okně **Vlastnosti projektu.**

Jedna z metod `CSpyApp` ve třídě vytváří upozornění na funkci, která již není podporována.

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

Varování je následující.

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

Zpráva WM_CTLCOLORDLG již byla zpracována v spy++ kódu, takže jedinou `SetDialogBkColor`požadovanou změnou bylo odstranění odkazů na , které již nejsou potřeba.

Další upozornění bylo jednoduché opravit komentováním názvu proměnné. Obdrželi jsme následující varování:

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

Kód, který to vytváří zahrnuje makro.

```cpp
DECODEPARM(CB_GETLBTEXT)
{
  P2WPOUT();

  P2LPOUTPTRSTR;
  P2IFDATA()
  {
    PARM(lpszBuffer, PPACK_STRINGORD, ED2);

    INDENT();

    P2IFISORD(lpszBuffer)
    {
      P2OUTORD(lpszBuffer);
    }
    else
    {
      PARM(lpszBuffer, LPTSTR, ED2);
      P2OUTS(lpszBuffer);
    }
  }
}
```

Velké použití maker jako v tomto kódu má tendenci ztížit údržbu kódu. V tomto případě makra obsahují deklarace proměnných. Makro PARM je definováno takto:

```cpp
#define PARM(var, type, src)type var = (type)src
```

Proto `lpszBuffer` proměnná získá deklarován dvakrát ve stejné funkci. Není to tak jednoduché opravit, jak by to bylo, kdyby kód nepoužíval makra (jednoduše odeberte deklaraci druhého typu). Jak to je, máme nešťastnou volbu, zda se musí rozhodnout, zda přepsat kód makra jako běžný kód (zdlouhavý a případně chyba náchylné k úkolu) nebo zakázat upozornění.

V takovém případě se rozhodneme upozornění zakázat. Můžeme to udělat přidáním pragma takto:

```cpp
#pragma warning(disable : 4456)
```

Při zakázání upozornění, můžete chtít omezit efekt zakázání pouze kód, který vytváří upozornění, aby se zabránilo potlačení upozornění, když může poskytnout užitečné informace. Přidáme kód pro obnovení upozornění těsně za řádek, který jej vytváří, nebo ještě lépe, protože toto upozornění se`#pragma` vyskytuje v makru, použijte klíčové slovo **__pragma,** které funguje v makrech ( nefunguje v makrech).

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

Další upozornění vyžaduje některé revize kódu. Rozhraní API `GetVersion` (a) `GetVersionEx`je zastaralé.

```Output
warning C4996: 'GetVersion': was declared deprecated
```

Následující kód ukazuje, jak je získána verze.

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

Následuje mnoho kódu, který zkoumá hodnotu dwWindowsVersion k určení, zda jsme spuštěni v systému Windows 95 a jakou verzi systému Windows NT. Vzhledem k tomu, že je to všechno zastaralé, odstraníme kód a vypořádáme se s odkazy na tyto proměnné.

Článek [Změny verze operačního systému v systémech Windows 8.1 a Windows Server 2012 R2](/windows/win32/w8cookbook/operating-system-version-changes-in-windows-8-1) vysvětlují situaci.

Ve `CSpyApp` třídě jsou metody, které dotazují na verzi operačního systému: `IsWindows9x`, `IsWindows4x`a `IsWindows5x`. Dobrým výchozím bodem je předpokládat, že verze systému Windows, které máme v úmyslu podporovat (Windows 7 a novější) jsou všechny v blízkosti Windows NT 5, pokud jde o technologie používané touto starší aplikací se týká. Použití těchto metod bylo řešit omezení starších operačních systémů. Tak jsme změnili tyto `IsWindows5x` metody vrátit TRUE pro a FALSE pro ostatní.

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

To zanechalo jen několik míst, kde byly vnitřní proměnné použity přímo. Vzhledem k tomu, že jsme tyto proměnné odstranili, dostaneme několik chyb, které musí explicitně řešit.

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

Mohli bychom jej nahradit voláním metody nebo jednoduše předat TRUE a odstranit staré zvláštní pouzdro pro systém Windows 9x.

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

Poslední varování na výchozí úrovni (3) má co do činění s bitfield.

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

Kód, který aktivuje toto je následující.

```cpp
m_bStdMouse = TRUE;
```

Deklarace `m_bStdMouse` označuje, že se jedná o bitfield.

```cpp
class CTreeListBox : public CListBox
{
  DECLARE_DYNCREATE(CTreeListBox)

  CTreeListBox();

  private:
  int ItemFromPoint(const CPoint& point);

  class CTreeCtl* m_pTree;
  BOOL m_bGotMouseDown : 1;
  BOOL m_bDeferedDeselection : 1;
  BOOL m_bStdMouse : 1;
```

Tento kód byl napsán před předdefinovaným typem bool byl podporován v jazyce Visual C++. V takovém kódu bool byl **typedef** pro **int**. Typ **int** je **podepsaný** typ a bitová reprezentace **podepsanéint** je použít první bit jako znaménkový bit, takže bitové pole typu int může být interpretováno jako představující 0 nebo -1, pravděpodobně není to, co bylo zamýšleno.

Při pohledu na kód byste nevěděli, proč se jedná o bitfields. Byl záměr zachovat velikost objektu malé, nebo je tam kdekoli, kde se používá binární rozložení objektu? Změnili jsme je na obyčejné členy BOOL, protože jsme neviděli žádný důvod pro použití bitfieldu. Použití bitových polí k zachování malé velikosti objektu není zaručeno, že bude fungovat. Záleží na tom, jak kompilátor stanoví typ.

Možná se divíte, jestli použití standardního typu **bool** v celém by bylo užitečné. Mnoho starých vzorů kódu, jako je například typ BOOL, bylo vynalezeno k řešení problémů, které byly později vyřešeny ve standardním jazyce C++, takže přechod z BOOL na vestavěný typ **bool** je jen jedním příkladem takové změny, kterou považujete za práci poté, co získáte kód, který byl původně spuštěn v nové verzi.

Jakmile jsme se zabývali všemi varováními, která se zobrazují na výchozí úrovni (úroveň 3), změnili jsme se na úroveň 4, abychom zachytili několik dalších upozornění. První, kdo se objevil, byl následující:

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

Kód, který vytvořil toto upozornění bylo následující.

```cpp
virtual void OnSelectTab(int nTab) {};
```

To se zdá neškodné dost, ale `/W4` `/WX` protože jsme chtěli čistou kompilaci a nastavit, jsme prostě komentoval i variabilní název, takže je kvůli čitelnosti.

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

Další upozornění, která jsme obdrželi, byla užitečná pro vyčištění obecného kódu. Existuje celá řada implicitní převody z **int** nebo **nepodepsané int** do aplikace WORD (což je typedef pro **nepodepsané krátké**). Jedná se o možnou ztrátu dat. V těchto případech jsme do aplikace WORD přidali obsazení.

Další úroveň 4 varování jsme dostali pro tento kód byl:

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

K problému dochází, když byla proměnná nejprve deklarována **extern**, později deklarována **jako statická**. Význam těchto dvou specifikátorů třídy úložiště se vzájemně vylučuje, ale to je povoleno jako rozšíření společnosti Microsoft. Pokud byste chtěli, aby byl kód přenosný pro jiné kompilátory, nebo jste ho chtěli zkompilovat pomocí (kompatibilita ANSI), `/Za` změnili byste deklarace tak, aby měly odpovídající specifikátory třídy úložiště.

## <a name="step-11-porting-from-mbcs-to-unicode"></a><a name="porting_to_unicode"></a>Krok 11. Přenos z mcrs do unicode

Všimněte si, že ve světě Windows, když říkáme Unicode, obvykle máme na mysli UTF-16. Jiné operační systémy, jako je Linux, používají UTF-8, ale Windows obecně ne. MBCS verze knihovny MFC byla zastaralá v sadě Visual Studio 2013 a 2015, ale již není zastaralá v sadě Visual Studio 2017. Pokud používáte Visual Studio 2013 nebo 2015, před provedením kroku skutečně port mbcs kód UTF-16 Unicode, můžeme chtít dočasně odstranit upozornění, že MBCS je zastaralé, aby bylo možné provést jinou práci nebo odložit portování až do vhodného času. Aktuální kód používá mbcs a pokračovat s tím, že je třeba nainstalovat ANSI/MBCS verzi knihovny MFC. Poměrně velká knihovna knihovny MFC není součástí výchozího vývoje sady Visual Studio Desktop s instalací **jazyka C++,** takže musí být vybrána z volitelných součástí v instalačním programu. Viz [Doplněk Knihovny MFC MBCS DLL](../mfc/mfc-mbcs-dll-add-on.md). Po stažení a restartování sady Visual Studio můžete zkompilovat a propojit s verzí knihovny MBCS, ale chcete-li se zbavit upozornění na knihovnu MBCS, pokud používáte sadu Visual Studio 2013 nebo 2015, měli byste také přidat NO_WARN_MBCS_MFC_DEPRECATION do seznamu předdefinovaných maker v části **Preprocesor** vlastností projektu nebo na začátku souboru záhlaví *stdafx.h* nebo jiného společného souboru záhlaví.

Nyní máme některé chyby propojovacího eru.

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

LNK1181 dochází, protože zastaralé statické knihovny verze mfc je součástí propojovacího programu vstup. To již není nutné, protože můžeme dynamicky propojit knihovnu MFC, takže stačí odebrat všechny statické knihovny knihovny MFC z **input** vlastnosti v **propojovací** mantineru vlastností projektu. Tento projekt také `/NODEFAULTLIB` používá možnost a místo toho obsahuje seznam všech závislostí knihovny.

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

Nyní nám skutečně aktualizovat starý multi-byte znaková sada (MBCS) kód Unicode. Vzhledem k tomu, že se jedná o aplikaci systému Windows, která je úzce spojena s platformou pro stolní počítače Windows, přeneseme ji na Unicode UTF-16, který systém Windows používá. Pokud píšete kód pro více platforem nebo portujete aplikaci systému Windows na jinou platformu, můžete zvážit přenesení na UTF-8, který je široce používán v jiných operačních systémech.

Porting na UTF-16 Unicode, musíme se rozhodnout, zda chceme stále možnost kompilovat mbcs nebo ne.  Pokud chceme mít možnost podporovat MBCS, měli bychom použít makro TCHAR jako typ znaku, který \_se překládá \_na **char** nebo **wchar_t**, v závislosti na tom, zda mbcs nebo UNICODE je definována během kompilace. Přepnutí na TCHAR a TCHAR verze různých rozhraní API namísto **wchar_t** a jeho přidružené rozhraní API znamená, že \_můžete vrátit k \_verzi MBCS kódu jednoduše definováním makra MBCS namísto UNICODE. Kromě TCHAR existuje řada verzí TCHAR, jako jsou široce používané typedefs, makra a funkce. Například LPCTSTR místo LPCSTR a tak dále. V dialogovém okně vlastností projektu v části **Vlastnosti konfigurace**v části **Obecné** změňte vlastnost **Znaková sada** z **příkazu Použít znakovou sadu MBCS** na **Použít znakovou sadu Unicode**. Toto nastavení ovlivňuje, které makro je během kompilace předdefinováno. K dispozici je makro UNICODE i makro \_UNICODE. Vlastnost projektu ovlivňuje oba konzistentně. Hlavičky systému Windows používají UNICODE, kde hlavičky \_Visual C++, jako je například knihovna MFC, používají UNICODE, ale když je jeden definován, druhý je vždy definován.

Existuje dobrý [průvodce](/previous-versions/cc194801(v=msdn.10)) portováním z MBCS na UTF-16 Unicode pomocí TCHAR. Tuto trasu volíme. Nejprve změníme vlastnost **Znaková sada** na **Použít znakovou sadu Unicode** a znovu vytvoříme projekt.

Některá místa v kódu již používali TCHAR, zřejmě v očekávání, že nakonec podpoří Unicode. Někteří ne. Hledali jsme instance CHAR, což je **typedef** pro **char**, a nahradil většinu z nich s TCHAR. Také jsme hledali `sizeof(CHAR)`. Kdykoli jsme změnili z CHAR na TCHAR, obvykle jsme museli změnit, `sizeof(TCHAR)` protože to bylo často používáno k určení počtu znaků v řetězci. Použití nesprávného typu zde nevytváří chybu kompilátoru, takže stojí za to věnovat tomuto případu trochu pozornosti.

Tento typ chyby je velmi častý hned po přepnutí na Unicode.

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

Tady je příklad kódu, který vytváří toto:

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

Dali \_jsme T kolem řetězce literálu odstranit chybu.

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

Makro \_T má za následek vytvoření literálu řetězce kompilovat jako **char** řetězec nebo **řetězec wchar_t,** v závislosti na nastavení MBCS nebo UNICODE. Chcete-li nahradit \_všechny řetězce písmenem T v sadě Visual Studio, nejprve otevřete pole **Rychlá výměna** (Klávesnice: **Klávesa Ctrl**+**F)** nebo **Nahradit v souborech** (Klávesnice: **Klávesa Ctrl**+**H)**+**H**a pak zaškrtněte políčko **Použít regulární výrazy.** Zadejte `((\".*?\")|('.+?'))` jako hledaný text a `_T($1)` jako náhradní text. Pokud již máte \_makro T kolem některých řetězců, tento postup jej znovu přidá a může \_také najít případy, `#include`kdy nechcete T, například při použití , takže je nejlepší použít **nahradit další** spíše než **Nahradit vše**.

Tato konkrétní funkce [wsprintf](/windows/win32/api/winuser/nf-winuser-wsprintfw), je ve skutečnosti definována v záhlaví systému Windows a dokumentace pro něj doporučuje, aby nebyla použita z důvodu možného přetečení vyrovnávací paměti. Pro `szTmp` vyrovnávací paměť není uvedena žádná velikost, takže neexistuje žádný způsob, jak funkce zkontrolovat, zda vyrovnávací paměť může obsahovat všechna data, která mají být zapsána do něj. Podívejte se na další část o přenosu do zabezpečeného CRT, ve které řešíme další podobné problémy. Nakonec jsme ho nahradili [_stprintf_s.](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)

Další častou chybou, kterou uvidíte při převodu na Unicode, je tato.

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

Kód, který jej vytváří, je následující:

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

I když `_tcscpy` byla použita funkce, což je funkce TCHAR strcpy pro kopírování řetězce, vyrovnávací paměť, která byla přidělena, byla **vyrovnávací paměť.** To je snadno změnit na TCHAR.

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Podobně jsme změnili LPSTR (dlouhý ukazatel na STRing) a LPCSTR (dlouhý ukazatel na konstantní STRing) na LPTSTR (dlouhý ukazatel na TCHAR STRing) a LPCTSTR (dlouhý ukazatel na konstantní TCHAR STRing), pokud je to zaručeno chybou kompilátoru. Rozhodli jsme se, že takové náhrady neprovedeme pomocí globálního vyhledávání a nahrazení, protože každá situace musela být přezkoumána individuálně. V některých případech char **verze** je chtěl, například při zpracování některých zpráv systému Windows, které používají struktury systému Windows, které mají příponu **A.** V rozhraní API systému Windows přípona **A** znamená ASCII nebo ANSI (a platí také pro MBCS) a přípona **W** znamená široké znaky nebo UTF-16 Unicode. Tento vzor pojmenování se používá v záhlaví systému Windows, ale také jsme postupovali v kódu Spy ++, když jsme museli přidat unicode verzi funkce, která byla již definována pouze ve verzi MBCS.

V některých případech jsme museli nahradit typ použít verzi, která řeší správně (WNDCLASS místo WNDCLASSA například).

V mnoha případech jsme museli použít obecnou verzi (makro) `GetClassName` rozhraní API `GetClassNameA`Win32 jako (místo ). V příkazu přepínače obslužné rutiny zprávy jsou některé zprávy specifické pro mbcs nebo unicode, v těchto případech jsme museli změnit kód explicitně volat verzi MBCS, protože jsme nahradili obecně pojmenované funkce specifickými pro **A** a **W** a přidali makro pro obecný název, který řeší správný název **A** nebo **W** na základě toho, zda je definován UNICODE.  V mnoha částech kódu, když jsme \_přešli na definici UNICODE, verze W je nyní vybrána i v případě, že verze **A** je to, co je chtěl.

Existuje několik míst, kde musely být podniknuty zvláštní akce. Jakékoli použití `WideCharToMultiByte` `MultiByteToWideChar` nebo může vyžadovat bližší pohled. Zde je jeden `WideCharToMultiByte` příklad, kde byl používán.

```cpp
BOOL C3dDialogTemplate::GetFont(CString& strFace, WORD& nFontSize)
{
  ASSERT(m_hTemplate != NULL);

  DLGTEMPLATE* pTemplate = (DLGTEMPLATE*)GlobalLock(m_hTemplate);
  if ((pTemplate->style & DS_SETFONT) == 0)
  {
    GlobalUnlock(m_hTemplate);
    return FALSE;
  }

  BYTE* pb = GetFontSizeField(pTemplate);
  nFontSize = *(WORD*)pb;
  pb += sizeof (WORD);
  WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
  strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
  strFace.ReleaseBuffer();
  GlobalUnlock(m_hTemplate);
  return TRUE;
}
```

Abychom to vyřešili, museli jsme pochopit, že důvodem, proč to bylo provedeno, bylo zkopírovat široký řetězec znaků představující název písma do vnitřní vyrovnávací paměti `CString`, `strFace`. To vyžadovalo mírně odlišný kód `CString` pro vícebajtové řetězce jako pro řetězce širokých znaků, `CString` takže jsme v tomto případě přidali. `#ifdef`

```cpp
#ifdef _MBCS
WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
strFace.ReleaseBuffer();
#else
wcscpy(strFace.GetBufferSetLength(LF_FACESIZE), (LPCWSTR)pb);
strFace.ReleaseBuffer();
#endif
```

Samozřejmě, místo `wcscpy` toho, `wcscpy_s`abychom opravdu měli používat , bezpečnější verze. Další část se zabývá tímto.

Jako kontrolu naší práce bychom měli obnovit **znakovou sadu,** abychom **používali vícebajtovou znakovou sadu** a ujistili se, že kód stále kompiluje pomocí MBCS a Unicode. Netřeba dodávat, že úplný testovací průchod by měl být proveden v překompilované aplikaci po všech těchto změnách.

V naší práci s tímto spy++ řešením trvalo asi dva pracovní dny, než průměrný vývojář c++ převedl kód na Unicode. To nezahrnovalo dobu opakovaného testování.

## <a name="step-12-porting-to-use-the-secure-crt"></a><a name="porting_to_secure_crt"></a>Krok 12. Přenos pro použití zabezpečeného crt

Porting kód používat zabezpečené verze (verze s **_s** příponou) crt funkcí je další. V tomto případě je obecnou strategií nahradit funkci **_s** verzí a pak obvykle přidat požadované další parametry velikosti vyrovnávací paměti. V mnoha případech je to jednoduché, protože velikost je známa. V ostatních případech, kde velikost není okamžitě k dispozici, je nutné přidat další parametry funkce, která používá funkci CRT, nebo možná zkontrolujte použití cílové vyrovnávací paměti a zjistěte, jaké jsou příslušné limity velikosti.

Visual C++ poskytuje trik, který usnadňuje zabezpečení kódu bez přidání tolika parametrů velikosti, a to pomocí přetížení šablony. Vzhledem k tomu, že tyto přetížení jsou šablony, jsou k dispozici pouze při kompilaci jako C ++, ne jako C. Spyxxhk je projekt C, takže trik nebude fungovat.  Nicméně, Spyxx není a můžeme použít trik. Trik je v tom, přidat řádek, jako je tento v místě, kde bude sestaven v každém souboru projektu, například v stdafx.h:

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

Když definujete, že vždy, když vyrovnávací paměť je pole, nikoli nezpracovaná ukazatel, jeho velikost je odvozena z typu pole a který se používá jako parametr velikosti, aniž byste museli zadat. To pomáhá snížit složitost přepisování kódu. Stále musíte nahradit název funkce **_s** verze, ale to lze často provést operací vyhledávání a nahrazení.

Vrácené hodnoty některých funkcí se změnily. Například `_itoa_s` (a `_itow_s` a `_itot_s`makro ) vrátí`errno_t`kód chyby ( ), nikoli řetězec. Takže v těchto případech budete muset `_itoa_s` přesunout volání na samostatný řádek a nahradit jej identifikátorem vyrovnávací paměti.

Některé běžné případy: `memcpy`pro , při `memcpy_s`přechodu na , jsme často přidali velikost struktury, které jsou kopírovány do. Podobně pro většinu řetězců a vyrovnávacích pamětí velikost pole nebo vyrovnávací paměti je snadno určena z deklarace vyrovnávací paměti nebo zjištěním, kde byla původně přidělena vyrovnávací paměť. V některých situacích je třeba určit, jak velká vyrovnávací paměť je skutečně k dispozici, a pokud tyto informace není k dispozici v oboru funkce, kterou upravujete, by měly být přidány jako další parametr a volající kód by měl být upraven tak, aby informace.

S těmito technikami trvalo asi půl dne převést kód používat zabezpečené funkce CRT. Pokud se rozhodnete ne přetížení šablony a přidat parametry velikosti ručně, bude pravděpodobně trvat dvakrát nebo třikrát více času.

## <a name="step-13-zcforscope--is-deprecated"></a><a name="deprecated_forscope"></a>Krok 13. /Zc:forScope- je zastaralé

Vzhledem k tomu, Visual C++ 6.0 kompilátor odpovídá aktuální standard, který omezuje rozsah proměnných deklarovaných ve smyčce na rozsah smyčky. Možnost kompilátoru [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**Force Conformance for Loop Scope** ve vlastnostech projektu) určuje, zda je tato možnost hlášena jako chyba. Měli bychom aktualizovat náš kód, aby byl konformní, a přidat deklarace těsně mimo smyčku. Chcete-li se vyhnout provádění změn kódu, **Language** můžete toto nastavení změnit `No (/Zc:forScope-)`v části Jazyk ve vlastnostech projektu jazyka C++ na . Mějte však `/Zc:forScope-` na paměti, že může být odebrána v budoucí verzi Visual C ++, takže nakonec váš kód bude muset změnit tak, aby odpovídaly standardu.

Tyto problémy jsou poměrně snadno opravit, ale v závislosti na kódu, může ovlivnit velké množství kódu. Zde je typický problém.

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

Výše uvedený kód vytváří chybu:

```Output
'n': undeclared identifier
```

K tomu dochází, protože kompilátor má zastaralé možnost kompilátoru, který povolil kód, který již není v souladu se standardem C++. Ve standardu deklarování proměnné uvnitř smyčky omezuje její rozsah pouze na smyčku, takže běžná praxe použití čítače smyčky mimo smyčku vyžaduje, aby deklarace čítače byla také přesunuta mimo smyčku, jako v následujícím revidovaném kódu:

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  int n;
  for (n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

## <a name="summary"></a>Souhrn

Portování Spy++ z původního kódu Visual C++ 6.0 na nejnovější kompilátor trvalo přibližně 20 hodin kódování v průběhu asi týdne. Upgradovali jsme přímo prostřednictvím osmi verzí produktu z Visual Studia 6.0 na Visual Studio 2015. Toto je nyní doporučený přístup pro všechny upgrady na projekty velké i malé.

## <a name="see-also"></a>Viz také

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Předchozí případová studie: COM Spy](../porting/porting-guide-com-spy.md)
