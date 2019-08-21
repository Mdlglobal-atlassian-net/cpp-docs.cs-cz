---
title: 'Průvodce přenosem: Spy++'
ms.date: 11/19/2018
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
ms.openlocfilehash: 175f3fbba7e18f625dc3425c236162737689f068
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630451"
---
# <a name="porting-guide-spy"></a>Průvodce přenosem: Spy++

Tato studijní událost je navržena tak, aby vám poskytla představu o typickém způsobu, jakým je projekt pro přenos, typy problémů, se kterými se můžete setkat, a některé obecné tipy a triky pro řešení problémů s přenosem. Nejedná se o nepostradatelného průvodce pro přenos, protože prostředí pro přenos projektu závisí hodně na konkrétních verzích kódu.

## <a name="spy"></a>Spy++

Spy + + je široce používaný diagnostický nástroj GUI pro stolní počítače s Windows, který poskytuje nejrůznější informace o prvcích uživatelského rozhraní na ploše Windows. Zobrazuje kompletní hierarchii Windows a poskytuje přístup k metadatům týkajícím se jednotlivých oken a ovládacích prvků. Tato užitečná aplikace byla dodávána se sadou Visual Studio po řadu let. Našli jsme starou verzi, která byla naposledy zkompilována v jazyce C++ Visual 6,0 a byla předaná do sady visual Studio 2015. Prostředí sady Visual Studio 2017 by mělo být téměř identické.

Tento případ považujeme za typický pro portování desktopových aplikací pro Windows, které používají knihovnu MFC a Win32 API, zejména pro staré projekty, které nebyly aktualizovány s každou vydanou C++ verzí vizuálu C++ od Visual 6,0.

##  <a name="convert_project_file"></a>Krok 1. Převádí se soubor projektu.

Soubor projektu, dva staré soubory. DSW z Visual C++ 6,0, snadno převedené bez problémů, které vyžadují další pozornost. Jedním projektem je aplikace Spy + +. Druhý je SpyHk, napsaný v C, podpůrné knihovně DLL. Složitější projekty se nemusí upgradovat tak snadno, jak je popsáno [zde](../porting/visual-cpp-porting-and-upgrading-guide.md).

Po upgradu těchto dvou projektů náš řešení vypadalo takto:

![Řešení Spy&#43; &#43; ]řešení(../porting/media/spyxxsolution.PNG "&#43; Spy&#43; ")

Máme dva projekty, jeden s velkým počtem C++ souborů a další knihovnu DLL, která je napsaná v jazyce C.

##  <a name="header_file_problems"></a>Krok 2. Problémy se soubory hlaviček

Při sestavování nově převedeného projektu je jedním z prvních věcí, které často hledáte, je, že soubory hlaviček, které váš projekt používá, se nenašly.

Jeden ze souborů, které se nepodařilo najít v programu Spy + +, byl verstamp. h. Z hledání na internetu jsme zjistili, že pochází ze sady DAO SDK, což je zastaralá technologie dat. Chtěli bychom zjistit, jaké symboly se z tohoto souboru hlaviček používaly, abyste zjistili, jestli je tento soubor skutečně potřeba, nebo jestli tyto symboly byly definované jinde, takže jsme zapisovali deklaraci hlavičkového souboru a znovu zkompilujeme. Zapíná se pouze jeden libovolný symbol, který je třeba VER_FILEFLAGSMASK.

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

Nejjednodušší způsob, jak najít symbol v dostupných souborech k zahrnutí, je použít funkci **najít v souborech** (**CTRL**+ **+ SHIFT**+**F**) a **zadat C++ adresáře pro zahrnutí vizuálu**. Našli jsme ho v ntverp. h. Nahradili jsme verstamp. h, který je zahrnutý v ntverp. h a tato chyba zmizela.

##  <a name="linker_output_settings"></a>Krok 3. Nastavení linkeru Výstupní_soubor

Starší projekty někdy mají soubory umístěné v nekonvenčních umístěních, která můžou po upgradu způsobit problémy. V takovém případě je nutné do vlastností `$(SolutionDir)` projektu přidat do cesty **include** , aby bylo zajištěno, že Visual Studio může najít některé hlavičkové soubory, které jsou umístěny tam, nikoli do jedné ze složek projektu.

Nástroj MSBuild stížnosti na to, že vlastnost **Link. Výstupní_soubor** neodpovídá hodnotám **targetPath** a **TargetName** a vydává MSB8012.

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link. Výstupní_soubor** je výstup sestavení (exe, DLL, například), který je obvykle vytvořen z `$(TargetDir)$(TargetName)$(TargetExt)`, který dává cestu, název souboru a příponu. Toto je běžná Chyba při migraci projektů z starého nástroje pro sestavení C++ sady Visual Build (vcbuild. exe) na nový nástroj sestavení (MSBuild. exe). Vzhledem k tomu, že došlo ke změně nástroje sestavení v aplikaci Visual Studio 2010, může dojít k tomuto problému při každém migrování projektu před 2010 na verzi 2010 nebo novější. Základním problémem je, že Průvodce migrací projektu neaktualizuje hodnotu **Link. Výstupní_soubor** , protože není vždy možné určit, jakou má má být hodnota založena na dalších nastaveních projektu. Proto je obvykle nutné ručně nastavit. Další podrobnosti najdete v tomto [příspěvku](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) na blogu vizuálu C++ .

V tomto případě byl vlastnost **Link. Výstupní_soubor** v převedeném projektu nastavena na .\Debug\Spyxx.exe a .\Release\Spyxx.exe pro projekt Spy + + v závislosti na konfiguraci. Nejlepším tipem je jednoduše nahradit tyto hodnoty pevně zakódované hodnotou `$(TargetDir)$(TargetName)$(TargetExt)` pro **všechny konfigurace**. Pokud to nefunguje, můžete z něj přizpůsobit nebo změnit vlastnosti v sekci **Obecné** , kde jsou tyto hodnoty nastaveny (vlastnosti jsou **výstupní adresář**, **název cíle**a **cílové rozšíření**. Pamatujte, že pokud Zobrazovaná vlastnost používá makra, můžete v rozevíracím seznamu zvolit možnost **Upravit** a zobrazit tak dialogové okno, ve kterém se zobrazí konečný řetězec s provedenými náhradami maker. Kliknutím na tlačítko **makra** můžete zobrazit všechna dostupná makra a jejich aktuální hodnoty.

##  <a name="updating_winver"></a>Krok 4. Aktualizace cílové verze systému Windows

Další chyba značí, že verze WINVER již není v knihovně MFC podporována. WINVER pro systém Windows XP je 0x0501.

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

Systém Windows XP již není společností Microsoft podporován, takže i když je v aplikaci Visual Studio povoleno cílení, je třeba pro ně v aplikacích škálovat podporu a podpořit uživatele, aby přijali nové verze Windows.

Chcete-li se pokusit odstranit chybu, definujte program WINVER tím, že aktualizujete nastavení **vlastností projektu** na nejnižší verzi Windows, na kterou nyní chcete cílit. Seznam hodnot pro různé verze Windows najdete [tady](/windows/win32/WinProg/using-the-windows-headers).

Soubor *stdafx. h* obsahoval některé z těchto definicí makra.

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

WINVER se nastaví na Windows 7. Pokud použijete makro pro Windows 7 (_WIN32_WINNT_WIN7) místo samotné hodnoty (0x0601), je snazší kód přečíst později.

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

##  <a name="linker_errors"></a>Krok 5. Chyby linkeru

S těmito změnami projekt SpyHk (DLL) vytváří, ale vytváří chybu linkeru.

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

Vstupní bod pro knihovnu DLL by neměl být exportován. Vstupní bod je určen pouze zavaděčem při prvním načtení knihovny DLL do paměti, takže by neměl být v exportní tabulce, která je pro jiné volající. Stačí, abyste se ujistili, že k ní není připojená direktiva **__declspec (dllexport)** . V spyxxhk. c je musíme odebrat ze dvou míst, deklarace a definice `DLLEntryPoint`. Nikdy nevedl smysl použít tuto direktivu, ale předchozí verze linkeru a kompilátoru je neoznačí jako problém. Novější verze linkeru poskytují upozornění.

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

Projekt knihovny DLL jazyka C, SpyHK. dll, nyní sestaví a spojuje bez chyby.

##  <a name="outdated_header_files"></a>Krok 6. Zastaralé soubory hlaviček

V tuto chvíli začneme pracovat na hlavním spustitelném projektu, Spyxx.

Nenašlo se několik dalších souborů k zahrnutí: knihovny CTL3D. h a PENWIN. h. I když může být užitečné Hledat v Internetu, abyste mohli zjistit, co obsahuje hlavičku, někdy tyto informace nejsou užitečné. Zjistili jsme, že knihovny CTL3D. h byl součástí sady Exchange Development Kit a poskytuje podporu pro určitý styl ovládacích prvků ve Windows 95 a PENWIN. h se týká výpočetního výpočetního prostředí (zastaralý API) oken. V takovém případě jednoduše Zakomentovat `#include` řádek a zavedeme nedefinované symboly, které jsme provedli s verstamp. h. Vše, co souvisí s prostorovými ovládacími prvky nebo výpočetním computingem, bylo odebráno z projektu.

Vzhledem k tomu, že projekt s mnoha chybami kompilace, které se postupně odstraňují, není reálné najít všechna použití zastaralého rozhraní API hned po odebrání této `#include` direktivy. Nerozpoznali jsme ji okamžitě, ale místo toho se v některých dalších bodech stala chyba, že WM_DLGBORDER nebyl definován. Ve skutečnosti je to jen jeden z mnoha nedefinovaných symbolů, které pocházejí z knihovny CTL3D. h. Jakmile zjistíme, že se vztahuje k zastaralému rozhraní API, odebrali jsme všechny odkazy v kódu.

##  <a name="updating_iostreams_code"></a>Krok 7. Aktualizace starého kódu iostreams

Další chyba je společná se starým C++ kódem, který používá iostreams.

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

Problémem je, že se stará Knihovna iostreams odebrala a nahradila. Musíme nahradit starou iostreams novějšími standardy.

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

Tyto aktualizace zahrnují:

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

V této změně máme problémy s `ostrstream`, který se už nepoužívá. Příslušná náhrada je ostringstream –. Pokusíme se přidat **typedef** pro `ostrstream` , aby nedošlo ke změně kódu příliš daleko, alespoň jako začátek.

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

V současné době je projekt sestaven pomocí vícebajtové znakové sady (MBCS), takže **znak** je vhodný datový typ znaků. Chcete-li však dovolit snazší aktualizaci kódu na kódování UTF-16 `TCHAR`, aktualizujme to na, který překládá na **char** nebo **wchar_t** v závislosti na tom, zda je vlastnost **znakové sady** v nastavení projektu nastavena na znakovou sadu MBCS nebo Unicode.

Je třeba aktualizovat několik dalších částí kódu.  Nahradili jsme základní třídu `ios` pomocí `ios_base`a nahradili jsme ostream basic_ostream\<T >. Přidáme dvě další definice typedef a tato část se zkompiluje.

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

Použití těchto definice typedef je pouze dočasné řešení. V případě trvalého řešení můžeme aktualizovat jednotlivé odkazy na přejmenované nebo zastaralé rozhraní API.

Tady je další chyba.

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

Dalším problémem je, že `basic_stringbuf` `freeze` nemá metodu. Metoda se používá k zabránění nevrácení paměti ve staré `ostream`paměti. `freeze` Teď ji nepotřebujeme, abychom používali novou `ostringstream`. Volání můžeme odstranit `freeze`.

```cpp
//rdbuf()->freeze(0);
```

Následující dvě chyby nastaly na sousedících řádcích. První stížnost týkající se použití `ends`, což je stará `iostream` manipulátor v/v knihovny, která přidá do řetězce ukončovací znak null. Druhá z těchto chyb vysvětluje, že výstup `str` metody nelze přiřadit k ukazateli, který není typu const.

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

Použití nové knihovny `ends` datových proudů není potřeba, protože řetězec je vždycky zakončený hodnotou null, takže tento řádek je možné odebrat. Pro druhý problém je problém, že nyní `str()` nevrací ukazatel na pole znaků pro řetězec; `std::string` vrátí typ. Řešením pro druhý je změna typu na `LPCSTR` a `c_str()` použití metody pro vyžádání ukazatele.

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

Došlo k chybě, která nám v tomto kódu nastala zpráva s přehledem.

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

Makro mout překládá na `*g_pmout` , což je objekt typu. `mstream` Třída je odvozena z `std::basic_ostream<TCHAR>`třídy standardního výstupního řetězce. `mstream` Ale u \_T kolem řetězcového literálu, který jsme vložili do přípravy na převod do kódování Unicode, se rozlišení přetížení pro **operátor < <** nezdařila s následující chybovou zprávou:

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

K dispozici je **operátor, < <** definice, že tento druh chyby může být zastrašování. Po bližším sestavování v dostupných přetíženích vidíte, že většina z nich je nepodstatná a podrobněji `mstream` se v definici třídy podíváme na to, že v tomto případě by měla být volána Tato funkce.

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

Důvod, proč není volána, je, že řetězcový literál má typ `const wchar_t[10]` , jak vidíte na posledním řádku této dlouhé chybové zprávy, takže převod na ukazatel, který není typu const, není automatický. Tento operátor by však neměl upravovat vstupní parametr, takže vhodnější typ parametru je `LPCTSTR` (`const char*` při kompilaci jako znakové sady MBCS a `const wchar_t*` jako Unicode), nikoli `LPTSTR` (`char*` při kompilaci jako znakové sady MBCS a `wchar_t*` jako Unicode). Změnou této chyby opravte tuto chybu.

Tento typ konverze byl povolený v rámci staršího, méně striktního kompilátoru, ale další poslední změny v souladu vyžadují přesnější kód.

##  <a name="stricter_conversions"></a>Krok 8. Přísnější převody kompilátoru

Také se vám zobrazí mnoho chyb, jako jsou následující:

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

K této chybě dojde v mapě zpráv, která je jednoduše makrem:

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

V rámci definice tohoto makra uvidíme, že odkazuje na funkci `OnNcHitTest`.

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

Problém je nutné provést s neshodou v ukazateli na typy členských funkcí. Problém není převodem `CHotLinkCtrl` typu třídy na `CWnd` typ třídy, protože to je platný převod odvozený na základní. Problémem je návratový typ: UINT vs. ZÍSKÁNÍ VÝSLEDKU LRESULT. ZÍSKÁNÍ výsledku LRESULT překládá na LONG_PTR, což je 64 ukazatel nebo 32 ukazatel v závislosti na cílovém binárním typu, takže UINT se nepřevádí na tento typ. To není neobvyklé při upgradu kódu napsaného před 2005, protože návratový typ mnoha metod mapování zpráv se změnil z UINT na získání výsledku LRESULT v aplikaci Visual Studio 2005 jako součást změn kompatibility s 64. Typ vrácené změny z UINT v následujícím kódu změníte na získání výsledku LRESULT:

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

Po změně máme následující kód:

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

Vzhledem k tomu, že existuje zhruba deset výskytů této funkce v různých třídách odvozených od CWnd, je užitečné použít **Přejít na definici** (klávesnice: **F12**) a **Přejít na deklaraci** (klávesnice:CTRL+**F12**), když je ukazatel myši na funkci v editoru, který je vyhledá a přejde do nich z okna **najít nástroj symbol** . **Přechod na definici** je obvykle užitečnější z těchto dvou. Příkaz **Přejít na deklaraci** vrátí deklarace jiné než deklarace třídy, jako jsou deklarace třídy Friend nebo dopředné odkazy.

##  <a name="mfc_changes"></a>Krok 9. Změny knihovny MFC

Další chyba se týká také změněného typu deklarace a také se objevuje v makru.

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

Problém je, že druhý parametr `CWnd::OnActivateApp` změněn z HTASK na hodnotu DWORD. Tato změna nastala ve verzi 2002 sady Visual Studio, Visual Studio .NET.

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

Je potřeba aktualizovat deklarace OnActivateApp v odvozených třídách, a to takto:

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

V tuto chvíli je možné projekt zkompilovat. K dispozici je několik upozornění, ale je možné, že existují volitelné části upgradu, jako je například převod ze znakové sady MBCS na kódování Unicode nebo zvýšení zabezpečení pomocí zabezpečených funkcí CRT.

##  <a name="compiler_warnings"></a>Krok 10. Řeší se upozornění kompilátoru.

Chcete-li získat úplný seznam upozornění, měli byste **znovu sestavit vše** v řešení, nikoli běžné sestavení, a zajistit tak, že vše, co bylo zkompilováno, bude znovu zkompilováno, protože pouze zprávy upozornění z aktuální kompilace. Druhá otázka má přijmout aktuální úroveň upozornění nebo použít vyšší úroveň upozornění.  Při přenosu velkého množství kódu, obzvláště starý kód, může být vhodné použít vyšší úroveň upozornění.  Možná budete chtít začít s výchozí úrovní upozornění a pak zvýšit úroveň upozornění, aby se zobrazila všechna upozornění. Pokud použijete `/Wall`, zobrazí se v systémových hlavičkových souborech některá upozornění, takže spousta lidí `/W4` používá k získání většiny upozornění na svůj kód bez upozornění na systémová záhlaví. Pokud chcete, aby se upozornění zobrazovala jako chyby, přidejte `/WX` možnost. Tato nastavení jsou v části **C/C++**  v dialogovém okně **Vlastnosti projektu** .

Jedna z metod ve `CSpyApp` třídě vytvoří upozornění na funkci, která již není podporována.

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

Upozornění je následující.

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

Zpráva WM_CTLCOLORDLG již byla zpracována v kódu Spy + +, takže jedinou změnou je nutné odstranit všechny odkazy na `SetDialogBkColor`, které už nepotřebujete.

Další upozornění bylo jednoduché opravit zadáním komentáře k názvu proměnné. Dostali jsme následující upozornění:

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

Kód, který vytváří, zahrnuje makro.

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

Těžké použití maker jako v tomto kódu obvykle usnadňuje údržbu kódu. V tomto případě makra obsahují deklarace proměnných. Makro parametr je definováno následujícím způsobem:

```cpp
#define PARM(var, type, src)type var = (type)src
```

Proto je `lpszBuffer` proměnná deklarována dvakrát ve stejné funkci. Není to jasné, aby to bylo možné opravit, protože by kód nepoužíval makra (pouhým odebráním druhé deklarace typu). V takovém případě máme unfortunate možnost rozhodnout, zda přepsat kód makra jako běžný kód (únavné a případně potenciálně náchylné k chybám), nebo zakázat upozornění.

V takovém případě se na toto upozornění rozhodneme zakázat. Dá se to udělat přidáním direktivy pragma následujícím způsobem:

```cpp
#pragma warning(disable : 4456)
```

Pokud zakážete upozornění, můžete chtít omezit efekt zakazování jenom na kód, který vygeneruje upozornění, aby nedošlo k potlačení upozornění, když by mohlo poskytovat užitečné informace. Přidáváme kód pro obnovení upozornění hned za řádek, který ho vytvořil, nebo ještě lepší, protože k tomuto upozornění dochází v makru, použijte klíčové slovo **__pragma** , které funguje v makrech (`#pragma` nefunguje v makrech).

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

Další upozornění vyžaduje revizi kódu. Win32 API `GetVersion` (a `GetVersionEx`) jsou zastaralé.

```Output
warning C4996: 'GetVersion': was declared deprecated
```

Následující kód ukazuje, jak je získána verze.

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

Následuje spousta kódu, který prověří hodnotu dwWindowsVersion a zjistí, jestli je služba spuštěná v systému Windows 95 a jakou verzi Windows NT. Vzhledem k tomu, že toto je zastaralé, odebereme kód a budeme se zabývat odkazy na tyto proměnné.

Tento článek popisuje situaci, kdy se [mění verze operačního systému v Windows 8.1 a Windows Server 2012 R2](/windows/win32/w8cookbook/operating-system-version-changes-in-windows-8-1) .

Ve `CSpyApp` třídě existují metody, které dotazují na verzi operačního systému: `IsWindows9x`, `IsWindows4x`a `IsWindows5x`. Dobrým výchozím bodem je předpokládat, že verze Windows, které chceme podporovat (Windows 7 a novější), jsou téměř v systému Windows NT 5, a to i v případě, že se jedná o technologie používané touto starší aplikací. Použití těchto metod bylo zabývat s omezením pro starší operační systémy. Proto jsme tyto metody změnili tak, aby `IsWindows5x` vracely hodnoty true a false pro ostatní.

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

To opustilo pouze několik míst, kde byly použity interní proměnné přímo. Vzhledem k tomu, že jsme tyto proměnné odebrali, máme několik chyb, které je potřeba řešit explicitně.

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

Můžeme to nahradit voláním metody nebo jednoduše předat hodnotu TRUE a odebrat starý zvláštní případ pro systémy Windows 9x.

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

Konečné upozornění na výchozí úrovni (3) musí dělat s bitového pole.

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

Kód, který se spustí, je následující.

```cpp
m_bStdMouse = TRUE;
```

Deklarace `m_bStdMouse` označuje, že se jedná o bitového pole.

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

Tento kód byl napsán před tím, než byl v vizuálu C++podporován vestavěný typ bool. V takovém kódu byla BOOL logická hodnota pro **int**. Typ **int** je **podepsaný** typ a bitová reprezentace **podepsaného int** je použít první bitovou kopii jako bit znaménka, takže bitového pole typu int může být interpretován jako hodnota 0 nebo-1, pravděpodobně to není zamýšleno.

Nevíte, že byste si poznali kód, proč se jedná o bitová pole. Byl záměr zachovat velikost objektu malý nebo na místě, kde se používá binární rozložení objektu? Změnili jsme je na běžné logické členy, protože nevidíme žádný důvod pro použití bitového pole. Použití bitová pole k zachování malého velikosti objektu není zaručené pracovat. Závisí na tom, jak kompilátor vymezuje typ.

Je možné, že pokud použijete **logický typ bool** v celém rozsahu, budete užitečná. Mnohé ze starých vzorů kódu, jako je typ BOOL, byly vymysleli k řešení problémů, které byly později vyřešeny standardně C++, takže změna z bool na **celočíselný** typ je pouze jeden příklad takové změny, kterou považujete po získání kódu do itially spuštěná v nové verzi.

Až se podíváme na všechna upozornění, která se objeví na výchozí úrovni (úroveň 3), kterou jsme změnili na úroveň 4, abyste mohli zachytit několik dalších upozornění. První se zobrazí takto:

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

Kód, který vytvořil toto upozornění, byl následující.

```cpp
virtual void OnSelectTab(int nTab) {};
```

Zdá se, že je dost neškodný, ale vzhledem k `/W4` tomu `/WX` , že jsme chtěli vyčistit a nastavovat čistou kompilaci, jednoduše odvoláme název proměnné, ale v zájmu čitelnosti ji ponechali.

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

Další upozornění, která jsme obdrželi, byla užitečná pro obecné vyčištění kódu. Existuje několik implicitních převodů typu **int** nebo **unsigned int** na slovo (což je definice typu pro **znaménko short**). To zahrnuje možnou ztrátu dat. V těchto případech jsme do WORDu přidali přetypování.

Další upozornění úrovně 4, které jsme získali pro tento kód:

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

K tomuto problému dochází, pokud byla proměnná poprvé deklarována jako **extern**a později deklarována jako **statická**. Význam těchto dvou specifikátorů třídy úložiště je vzájemně exkluzivní, ale je povolen jako rozšíření společnosti Microsoft. Pokud jste chtěli, aby byl kód přenosný na jiné kompilátory nebo jste ho chtěli zkompilovat s `/Za` (kompatibilita ANSI), změňte deklarace tak, aby měly stejné specifikátory třídy úložiště.

##  <a name="porting_to_unicode"></a>Krok 11. Přenos ze znakové sady MBCS do kódování Unicode

Všimněte si, že ve Windows World říkáme Unicode, obvykle to znamená UTF-16. Jiné operační systémy, jako je Linux, používají UTF-8, ale Windows všeobecně ne. Verze znakové sady MFC byla v Visual Studio 2013 a 2015 zastaralá, ale už se nepoužívá v rámci sady Visual Studio 2017. Pokud používáte Visual Studio 2013 nebo 2015, než se pustíte do kódu znakové sady MBCS pro kódování UTF-16, můžeme dočasně eliminovat upozornění, že sada MBCS je zastaralá, aby bylo možné provést další práci nebo odložit přenos do vhodného času. Aktuální kód používá znakovou sadu MBCS a chcete-li pokračovat, je nutné nainstalovat verzi knihovny MFC ANSI/MBCS. Spíše Velká knihovna MFC není součástí výchozího vývojového prostředí sady Visual Studio **s C++**  instalací, takže musí být vybrána z volitelných součástí instalačního programu. Viz [doplněk MFC MBCS DLL](../mfc/mfc-mbcs-dll-add-on.md). Po stažení a restartování sady Visual Studio můžete kompilovat a propojit s verzí znakové sady MFC, ale chcete-li se zbavit upozornění na znakovou sadu MBCS, pokud používáte Visual Studio 2013 nebo 2015, měli byste také přidat NO_WARN_MBCS_MFC_DEPRECATION do seznamu předdefinovaných makra v oddílu **preprocesoru** vlastností projektu nebo na začátku souboru hlaviček *stdafx. h* nebo jiného společného hlavičkového souboru.

Teď máme chyby linkeru.

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

K LINKERŮ LNK1181 dochází, protože zastaralá verze statické knihovny MFC je obsažena ve vstupu linkeru. To už není nutné, protože můžeme dynamicky propojit knihovnu MFC, takže musíme pouze odebrat všechny statické knihovny knihovny MFC z vlastnosti **input** v oddílu **linker** vlastností projektu. Tento projekt také používá `/NODEFAULTLIB` možnost a místo toho uvádí všechny závislosti knihoven.

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

Nyní můžeme současně aktualizovat starý kód vícebajtové znakové sady (MBCS) na kódování Unicode. Vzhledem k tomu, že se jedná o aplikaci pro Windows, podrobnějším pohledu zjistíte se váže na desktopovou platformu Windows, pošle ji na kódování UTF-16, které Windows používá. Pokud píšete kód pro různé platformy nebo nasazujete aplikaci pro Windows na jinou platformu, můžete zvážit přenos do UTF-8, které se běžně používá v jiných operačních systémech.

Při přenosu do kódování UTF-16 je nutné rozhodnout, zda stále chcete možnost kompilovat do znakové sady MBCS nebo ne.  Pokud chceme mít možnost podporovat znakovou sadu MBCS, měli byste použít TCHAR makro jako typ znaku, který se přeloží na char nebo **wchar_t**v závislosti na tom, zda \_je při kompilaci definována \_ **znaková** sada MBCS nebo Unicode. Přechod na TCHAR a TCHAR verze různých rozhraní API namísto **wchar_t** a jeho přidružených rozhraní API znamená, že se můžete vrátit zpět k verzi kódu znakové sady MBCS jednoduše tak, že \_namísto \_kódování Unicode nadefinujete makro MBCS. Kromě TCHAR, existuje celá řada TCHARových verzí, jako je široce používané definice typedef, makra a funkce. Například LPCTSTR namísto LPCSTR a tak dále. V dialogovém okně Vlastnosti projektu v části **Vlastnosti konfigurace**v sekci **Obecné** změňte vlastnost **znaková sada** z **použití znakové sady znakové sady MBCS** na použít znakovou **sadu Unicode**. Toto nastavení má vliv na to, které makro je předdefinovaná během kompilace. K dispozici je makro Unicode a \_makro Unicode. Vlastnost projektu má vliv na obě konzistentně. Hlavičky systému Windows používají znakovou sadu C++ Unicode, kde vizuální záhlaví \_, jako je například MFC, používá kódování Unicode, ale když je definována, druhá je vždy definovaná.

Dobrý [návod](/previous-versions/cc194801(v=msdn.10)) k přenosu znakové sady MBCS na kódování UTF-16 pomocí TCHAR existuje. Zvolíme tuto trasu. Nejprve změníte vlastnost **znakové sady** na **použití znakové sady Unicode** a znovu sestavíte projekt.

Některá místa v kódu již používala TCHAR, zjevně při předvídání případné podpory kódování Unicode. Některé nebyly. Hledali jsme instance CHAR, což je **definice** typu char, a nahradili většinu těchto **znaků**pomocí TCHAR. Také jsme hledali `sizeof(CHAR)`. Pokaždé, když jsme změnili z char na TCHAR, obvykle jsme `sizeof(TCHAR)` se museli změnit na, protože se často používal k určení počtu znaků v řetězci. Pomocí nesprávného typu tady nevzniká Chyba kompilátoru, takže bude platit trochu pozornosti k tomuto případu.

Tento typ chyby je velmi běžný, jenom po přepnutí do kódování Unicode.

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

Zde je příklad kódu, který vytváří toto:

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

Vydáte \_T kolem řetězcového literálu, aby se chyba odstranila.

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

Makro T má vliv na to, že se má řetězcové literály kompilovat jako řetězec **znaků** nebo jako řetězec wchar_t v závislosti na nastavení znakové sady MBCS nebo Unicode. \_ Chcete-li nahradit všechny \_řetězce T v aplikaci Visual Studio, otevřete nejprve **rychlé nahrazení** (klávesnice:CTRL+**F**) nebo **nahradit v souborech** (klávesnice: **Stiskněte kombinaci kláves CTRL**+**SHIFT**+**H**) a potom zaškrtněte políčko **použít regulární výrazy** . Jako `((\".*?\")|('.+?'))` text pro hledání zadejte text `_T($1)` a jako náhradní text. Pokud již máte \_makro T kolem některých řetězců, tento postup ho znovu přidá a může také najít případy, kdy nechcete \_T, například při použití `#include`, takže je nejvhodnější použít místo  **Nahradit vše**.

Tato konkrétní funkce, [wsprintf](/windows/win32/api/winuser/nf-winuser-wsprintfw), je ve skutečnosti definována v hlavičkách systému Windows a dokumentace pro IT doporučuje, aby se nepoužila kvůli možnému přetečení vyrovnávací paměti. Pro `szTmp` vyrovnávací paměť není přidělena žádná velikost, a proto není možné, aby funkce kontrolovala všechna data, která mají být zapsána do vyrovnávací paměti. Přečtěte si další část týkající se přenosu do zabezpečeného CRT, ve kterém řešíme jiné podobné problémy. Ukončili jsme nahrazení pomocí [_stprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).

Další běžná chyba se zobrazí při převodu do kódování Unicode.

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

Kód, který vytváří, je následující:

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

I když `_tcscpy` byla funkce použita, což je funkce TCHAR strcpy pro kopírování řetězce, přidělená vyrovnávací paměť byla znaková vyrovnávací paměť. Tato možnost se snadno mění na TCHAR.

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

Podobně jsme změnili typem LPStr (dlouhý ukazatel na řetězec) a LPCSTR (dlouhý ukazatel na konstantní řetězec) na LPTSTR (dlouhý ukazatel na TCHAR STRing) a LPCTSTR (dlouhý ukazatel na konstantní řetězec TCHAR), pokud je to odůvodněné chybou kompilátoru. Zvolili jsme, že tyto náhrady neprovedeme pomocí globálního vyhledávání a nahrazení, protože každou situaci museli prozkoumat jednotlivě. V některých případech je třeba použít **znak** verze, například při zpracování určitých zpráv systému Windows, které používají struktury systému Windows, které mají příponu. V rozhraní API systému Windows přípona **a** znamená ASCII nebo ANSI (a také platí pro znakovou sadu MBCS) a přípona **W** znamená velké znaky nebo kódování UTF-16. Tento vzor pro pojmenování se používá v hlavičkách systému Windows, ale také jsme ho použili v kódu Spy + +, když jsme museli přidat verzi Unicode funkce, která už je definovaná jenom ve verzi znakové sady MBCS.

V některých případech jsme museli nahradit typ pro použití verze, která se správně vyřeší (například WNDCLASS namísto WNDCLASSA).

V mnoha případech jsme museli používat obecnou verzi (makro) Win32 API, jako `GetClassName` je ( `GetClassNameA`místo). V příkazu přepínače obslužné rutiny zpráv je možné, že některé zprávy jsou specifické pro znakovou sadu MBCS nebo Unicode. v těchto případech jsme museli změnit kód tak, aby explicitně volal verzi znakové sady MBCS, protože nahradili jsme obecně pojmenované funkce pomocí specifických funkcí a. a přidání makra pro obecný název, který se přeloží na správný název nebo nebo **W** na základě toho, zda je kódování Unicode definováno.  V mnoha částech kódu, když jsme přešli k definování \_Unicode, se teď verze W vybere i v případě, že verze **A** je to, co je žádoucí.

Je k dispozici několik míst, kde byly provedeny zvláštní akce. Jakékoli použití `WideCharToMultiByte` nebo `MultiByteToWideChar` může vyžadovat užší vzhled. Tady je jeden příklad, `WideCharToMultiByte` kde se používá.

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

Abychom to vyřešili, museli jsme porozumět tomu, že k tomuto účelu bylo nutné zkopírovat řetězec s velkým počtem znaků, který představuje název písma, `CString` `strFace`do vnitřní vyrovnávací paměti a. To je trochu odlišný kód pro vícebajtové `CString` řetězce jako u řetězců s velkým znakem `CString` `#ifdef` , takže jsme v tomto případě přidali v tomto případě.

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

Samozřejmě místo toho `wcscpy` byste měli používat `wcscpy_s`bezpečnější verzi. V další části se tento oddíl adresuje.

V rámci kontroly naší práce by se měla resetovat **znaková sada** , aby **používala vícebajtovou znakovou sadu** , a ujistěte se, že kód stále kompiluje pomocí znakové sady MBCS i Unicode. Bez nutnosti vyslovit úplný test průchodu by měl být spuštěn v Rekompilované aplikaci po všech těchto změnách.

V naší práci s tímto řešením Spy + + trvalo zhruba dva pracovní dny, než je průměrně C++ vývojář převést kód na kódování Unicode. Které nezahrnovaly dobu přezkoušení.

##  <a name="porting_to_secure_crt"></a>Krok 12. Přenos na použití zabezpečeného CRT

Portování kódu pro použití zabezpečených verzí (verze s příponou **_s** ) pro funkce CRT je další. V tomto případě je v obecné strategii náhrada funkce pomocí verze **_s** a pak obvykle přidejte požadované další parametry velikosti vyrovnávací paměti. V mnoha případech je to jednoduché, protože velikost je známá. V jiných případech, kde velikost není okamžitě k dispozici, je nutné přidat další parametry do funkce, která používá funkci CRT, nebo možná prošetřit využití cílové vyrovnávací paměti a zjistit, co je vhodné omezení velikosti.

Vizuál C++ poskytuje štych, který usnadňuje zabezpečení kódu bez nutnosti přidat tolik parametrů velikosti a to za použití přetížení šablony. Vzhledem k tomu, že tato přetížení jsou šablony, jsou k dispozici pouze C++při kompilaci jako, nikoli jako C. spyxxhk je projekt jazyka C, takže štych nebude pro to fungovat.  Spyxx ale není a můžeme použít štych. Štych je přidat řádek podobný tomuto jako místo, kde bude zkompilován v každém souboru projektu, například v Stdafx. h:

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

Definujete-li, že pokud je vyrovnávací paměť pole, spíše než nezpracovaný ukazatel, jeho velikost je odvozena z typu pole a je použita jako parametr velikosti, aniž byste je museli zadat. To pomáhá snížit složitost psaní kódu. Stále je nutné nahradit název funkce verzí **_s** , ale to je často provedeno operací vyhledávání a nahrazování.

Návratové hodnoty některých funkcí se změnily. Například `_itoa_s` (a `_itow_s` a makro `_itot_s`) vrátí kód chyby (`errno_t`) místo řetězce. Takže v těchto případech je nutné přesunout volání na `_itoa_s` samostatný řádek a nahradit ho identifikátorem vyrovnávací paměti.

Některé běžné případy: `memcpy`v případě, že při přechodu na `memcpy_s`, často jsme přidali velikost struktury, do které se kopíruje. Podobně pro většinu řetězců a vyrovnávací paměti je velikost pole nebo vyrovnávací paměti snadné určit z deklarace vyrovnávací paměti nebo hledáním, kde byla vyrovnávací paměť původně přidělena. V některých situacích potřebujete určit, jak velká část vyrovnávací paměti je skutečně k dispozici, a pokud tyto informace nejsou k dispozici v rozsahu funkce, kterou upravujete, měla by být přidána jako další parametr a volající kód by měl být změněn na Zadejte informace.

Tyto techniky trvalo přibližně půl dne, aby se kód převedl na použití zabezpečených funkcí CRT. Pokud se rozhodnete, že se nejedná o přetížení šablony a ruční přidání parametrů velikosti, bude pravděpodobně trvat dvakrát nebo třikrát více času.

##  <a name="deprecated_forscope"></a>Krok 13. /Zc: forScope – je zastaralé.

Od verze C++ Visual 6,0 kompilátor odpovídá aktuálnímu standardu, který omezuje rozsah proměnných deklarovaných ve smyčce na rozsah smyčky. Možnost kompilátoru [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (vynutit**shodu oboru smyčky** ve vlastnostech projektu) řídí, zda je tato funkce hlášena jako chyba. Náš kód bychom měli aktualizovat tak, aby byl vyhovující, a přidat deklarace přímo mimo smyčku. Chcete-li se vyhnout provádění změn kódu, můžete změnit toto nastavení v části **jazyk** vlastností C++ projektu na. `No (/Zc:forScope-)` Mějte ale na paměti, že `/Zc:forScope-` v budoucí verzi vizuálu C++se může odebrat, takže je potřeba, aby se váš kód změnil, aby odpovídal standardu.

Tyto problémy je poměrně snadné opravit, ale v závislosti na vašem kódu může mít vliv na spoustu kódu. Tady je typický problém.

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

Výše uvedený kód vytvoří chybu:

```Output
'n': undeclared identifier
```

K tomu dochází, protože kompilátor uzavřel možnost kompilátoru s povoleným kódem, který již nedodržuje C++ Standard. Ve standardu deklarace proměnné uvnitř smyčky omezuje svůj rozsah pouze na smyčku, takže běžný postup použití počítadla smyčky mimo smyčku vyžaduje, aby deklarace čítače byla také přesunuta mimo smyčku, jak je uvedeno v následujícím změněném kódu. :

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

Portování nástroje Spy + + od původního kódu C++ Visual 6,0 k nejnovějšímu kompilátoru trvalo přibližně 20 hodin při kódování v průběhu přibližně týden. Provedli jsme upgrade přímo na osm vydání produktu ze sady Visual Studio 6,0 na Visual Studio 2015. To je teď doporučený postup pro všechny upgrady na projektech, které jsou velké a malé.

## <a name="see-also"></a>Viz také:

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Předchozí Případová studie: COM Spy](../porting/porting-guide-com-spy.md)
