---
title: 'Průvodce přenosem: Spy ++ | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebc7abdcdad1c44d0758100abdea96101fb68e52
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465358"
---
# <a name="porting-guide-spy"></a>Průvodce přenosem: Spy++
Tento přenos případovou studii – slouží k získáte představu o jaké typické přenosem projekt je jako typů problémů můžete setkat, a některé obecné tipy a triky pro účely řešení problémů s přenosem. Není má určené jako úplnou příručku k přenesení, protože funkce přenesení do projektu z velké části závisí na konkrétním kódu.  
  
## <a name="spy"></a>Spy++  
 
Spy ++ je často používaný diagnostický nástroj grafického uživatelského rozhraní pro plochu Windows, která poskytuje nejrůznější informace o prvcích uživatelského rozhraní na ploše Windows. Ukazuje kompletní hierarchie systému windows a poskytuje přístup k metadatům o každé okno a ovládací prvek. Tato aplikace užitečné byla odeslaná pomocí sady Visual Studio po mnoho let. Zjistili jsme, stará verze jeho poslední kompilaci v aplikaci Visual C++ 6.0 a přenést ho do sady Visual Studio 2015. Prostředí sady Visual Studio 2017 by měl být téměř shodné.
  
Společnost Microsoft považovat za tento případ jako typická pro portování aplikací klasické pracovní plochy Windows, používající knihovnu MFC a rozhraní API systému Win32, zejména u starých projektů, které nebyly aktualizovány s každou vydanou verzí jazyka Visual C++ od Visual C++ 6.0.  
  
##  <a name="convert_project_file"></a> Krok 1. Převádí se projektový soubor.  

Soubor projektu, dvě staré .dsw soubory Visual C++ 6.0, jednoduše převést bez problémů, které vyžadují další pozornost. Jeden projekt je aplikace nástroje Spy ++. Druhá je SpyHk napsané v jazyce C, podpůrné knihovny DLL. Složitější projekty upgradovat stejně snadno, jak je popsáno [tady](../porting/visual-cpp-porting-and-upgrading-guide.md).  
  
Po provedení upgradu dvou projektů, vypadal náš řešení toto:  
  
![Nástroji Spy&#43; &#43; řešení](../porting/media/spyxxsolution.PNG "SpyxxSolution")  
  
Máme dva projekty, jednu s velkým množstvím souborů C++ a další knihovny DLL, která je napsána v jazyce C.  
  
##  <a name="header_file_problems"></a> Krok 2. Hlavička souboru problémy  

Při vytváření nově převedeného projektu, jedním z prvních věcí, které se často stává je, že nebyly nalezeny soubory hlaviček, které používá váš projekt.  
  
Byl jeden ze souborů, které se nenašel v nástroji Spy ++ verstamp.h. Ze vyhledávání na Internetu můžeme určit, pochází ze sady SDK rozhraní DAO, technologie zastaralá data. Chtěli jsme se zjistit, jaké symboly byly použity z tohoto souboru záhlaví, zda tento soubor byl opravdu potřebujete, nebo pokud tyto symboly nebyly definovány jinde, takže můžeme zakomentované deklaraci záhlaví souboru a znovu zkompilovat. Ukazuje je jen jeden symbol, který je potřeba, VER_FILEFLAGSMASK.  
  
```  
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK  
```  
  
Nejjednodušší způsob, jak najít symbol v souborech zahrnutí k dispozici je použití **najít v souborech** (**Ctrl**+**Shift**+**F**) a zadejte **adresáře souborů k zahrnutí Visual C++**. Našli jsme ji v ntverp.h. Jsme nahradit verstamp.h zahrnout ntverp.h a zmizel k této chybě.  
  
##  <a name="linker_output_settings"></a> Krok 3. Nastavení OutputFile linkeru  

Starší projekty někdy nutné soubory umístěné v neobvyklé umístění, které mohou způsobovat problémy po dokončení upgradu. V tomto případě máme přidat `$(SolutionDir)` k **zahrnout** cestu ve vlastnostech projektu zajistit, že Visual Studio najdete některé soubory s hlavičkami, které jsou zde umístěny, nikoli v jednom ze složky projektu.  
  
MSBuild si bude stěžovat na, který **Link.OutputFile** vlastnost neodpovídá **TargetPath** a **TargetName** hodnoty vydávání MSB8012.  
  
```Output  
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).  
```  
  
**Link.OutputFile** je výstup sestavení (EXE, DLL, třeba) a je obvykle vytvořen z `$(TargetDir)$(TargetName)$(TargetExt)`, poskytuje cesty, názvu souboru a přípony. To je běžné chyby při migraci projektů ze staré Visual C++ sestavení nástroje (vcbuild.exe) nový nástroj pro sestavení (MSBuild.exe). Protože došlo ke změně nástroj pro sestavení v sadě Visual Studio 2010, můžete narazit na tento problém pokaždé, když se migrovat projekt Project 2010 2010 nebo novější verzi. Základní problém je, že v Průvodci projektem migrace neprovede aktualizaci **Link.OutputFile** hodnotu, protože není vždy možné určit, co by měl mít hodnotu na základě jiné nastavení projektu. Proto je obvykle nutné nastavit ručně. Další podrobnosti najdete v tomto [příspěvku](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) na blogu Visual C++.  
  
V takovém případě **Link.OutputFile** vlastnost v převedeného projektu byla nastavena na.\Debug\Spyxx.exe a.\Release\Spyxx.exe nástroje Spy ++ projektu, v závislosti na konfiguraci. Nejvhodnějších je jednoduše nahrazovat tyto hodnoty pevně zakódované `$(TargetDir)$(TargetName)$(TargetExt)` pro **všechny konfigurace**. Pokud to nepomůže, můžete upravit z něj nebo změny vlastností v **Obecné** části, kde jsou tyto hodnoty nastaveny (vlastnosti jsou **výstupní adresář**, **název cílového**, a **cílit na rozšíření**. Mějte na paměti, pokud vlastnost si prohlížíte používá makra, které můžete zvolit **upravit** v rozevíracím seznamu a zobrazte dialogové okno, které se zobrazují posledním řetězci uvedené s provedeny náhrady – makro. Všechna dostupná makra a jejich aktuální hodnoty můžete zobrazit výběrem **makra** tlačítko.  
  
##  <a name="updating_winver"></a> Krok 4. Aktualizuje se cílová verze Windows  

Další chyba udává, že verze WINVER již není podporována v knihovně MFC. Příkaz WINVER pro Windows XP je 0x0501.  
  
```Output  
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.  
```  
  
Windows XP je již nejsou podporovány společností Microsoft, takže i v případě, že její nastavení jako cíle může v sadě Visual Studio 2015, by měl být překážkou podporu pro ně ve svých aplikacích a podporu uživatelé přijmout nové verze Windows.  
  
 Chyba zbavit, definujte WINVER aktualizací **vlastnosti projektu** nastavení na nejnižší verze Windows aktuálně chcete cílit. Najít tabulku s hodnotami pro různé verze Windows [tady](/windows/desktop/WinProg/using-the-windows-headers).  
  
Souboru stdafx.h obsahovala některé z těchto definice maker.  
  
```cpp  
#define WINVER       0x0500  // these defines are set so that we get the  
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,  
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.    
```  
  
Příkaz WINVER nastavíme na Windows 7. Je snazší přečíst kód později použití makra pro Windows 7 (_WIN32_WINNT_WIN7), ne samotná (0x0601) hodnota.  
  
```cpp  
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7  
```  
  
##  <a name="linker_errors"></a> Krok 5. Chyby linkeru  

Tyto změny projektu SpyHk (DLL) sestavení, ale způsobí chybu linkeru.  
  
```  
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12  
```  
  
Vstupní bod pro knihovnu DLL se nesmí exportovat. Vstupní bod je určena pouze k zavaděčem volat, pokud knihovna DLL je prvním načtení do paměti, proto to nesmí být v exportní tabulce, která je pro ostatní volající. Potřebujeme Ujistěte se, že nemá **__declspec(dllexport)** – direktiva k němu připojená. V spyxxhk.c, musíme ho odebrat ze dvou míst, deklarace a definice `DLLEntryPoint`. Nikdy proveden použití této direktivy, ale předchozí verze kompilátoru a linkeru nelze označit jako problém. Novější verze linkeru poskytnout upozornění.  
  
```cpp  
// deleted __declspec(dllexport)  
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);    
```  
  
Projektu knihovny DLL jazyka C, SpyHK.dll, teď vytvoří a propojí bez chyb.  
  
##  <a name="outdated_header_files"></a> Krok 6. Více zastaralé soubory hlaviček  
 
V tuto chvíli můžeme začít pracovat na hlavní spustitelný projekt Spyxx.  
  
Nebyl nalezen pár dalších souborů k zahrnutí: ctl3d.h a penwin.h. Může být užitečné při hledání na Internetu a pokouší se určit, co zahrnuje záhlaví, někdy informace není to užitečné. Jsme zjistili, že ctl3d.h se součást Exchange Development Kit a zajistili podporu stylu ovládacích prvků ve Windows 95 a vztahuje se penwin.h okno pera výpočty, zastaralé rozhraní API. V tomto případě můžeme jednoduše komentář `#include` řádku a vypořádat se nedefinované symboly, jako jsme to udělali s verstamp.h. Vše, co souvisí s 3D ovládací prvky nebo pera computingu byla odebrána z projektu.  
  
Zadaný projekt s mnoha chyby kompilace, které jsou postupně vyloučení, není realistické najít všechna použití zastaralé rozhraní API, okamžitě, když odeberete `#include` směrnice. Jsme nezjistili to okamžitě, ale spíše na některé později přišel do chybu, že WM_DLGBORDER nebyla definovaná. Ve skutečnosti pouze jedna je mnoho nedefinované symboly, které pocházejí z ctl3d.h. Jakmile jsme jste zjistili, že má vztah k rozhraní API zastaralé, jsme odebrali všechny odkazy v kódu k němu.  
  
##  <a name="updating_iostreams_code"></a> Krok 7. Aktualizuje se starším kódem iostreams  
 
Další chyba je běžné u starého kódu C++, který používá iostreams.  
  
mstream.h(40): závažná chyba C1083: nejde otevřít vložený soubor: 'iostream.h': žádný odpovídající soubor nebo adresář  
  
Tento problém je, že původní knihovny iostreams byl odebrán a nahrazen. Máme nahraďte staré iostreams novější standardy.  
  
```cpp  
#include <iostream.h>  
#include <strstrea.h>  
#include <iomanip.h>    
```  
  
Jedná se o aktualizaci zahrnuje:  
  
```cpp  
#include <iostream>  
#include <sstream>  
#include <iomanip>    
```  
  
Díky této změně jsme, že máte problémy s `ostrstream`, který se už používá. Ostringstream je vhodné náhrada. Jsme zkuste přidat **typedef** pro `ostrstream` , aby změny kódu příliš mnoho alespoň jako spuštění.  
  
```cpp  
typedef std::basic_ostringstream<TCHAR> ostrstream;    
```  
  
Aktuálně je projekt vytvořen pomocí znakové sady MBCS (vícebajtovou znakovou sadu), takže **char** je datový typ odpovídající znak. Však umožňuje jednodušší aktualizace kódu Unicode UTF-16, aktualizujeme tuto hodnotu na `TCHAR`, která se přeloží na **char** nebo **wchar_t** podle toho, jestli **znaková sada** v nastavení projektu je nastavena na znakové sady MBCS a Unicode.  
  
Několik jiných částí kódu je potřeba aktualizovat.  Jsme nahradit základní třídy `ios` s `ios_base`, a jsme nahradit ostream je basic_ostream –\<T >. Přidáme dva další – definice TypeDef a zkompiluje v této části.  
  
```cpp  
typedef std::basic_ostream<TCHAR> ostream;  
typedef ios_base ios;    
```  
  
Pomocí těchto – definice TypeDef je pouze dočasné řešení. Pro více trvalé řešení může aktualizujeme každý odkaz na rozhraní API přejmenovaných nebo zastaralé.  
  
Tady je další chyba.  
  
```Output  
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'  
```  
  
Dalším problémem je, že `basic_stringbuf` nemá `freeze` metody. `freeze` Metoda se používá při prevenci nevracení paměti v původní `ostream`. Ten nepotřebujeme teď používáme nové `ostringstream`. Odstraníme volání `freeze`.  
  
```cpp  
//rdbuf()->freeze(0);  
```  
  
Sousední řádků došlo k následující dva chybám. Si bude stěžovat na první použití `ends`, což je starý `iostream` manipulátor vstupně-výstupních operací knihovny, který ukončovací znak null přidá na řetězec. Druhý z těchto chyb, který vysvětluje výstup `str` metody nelze přiřadit nekonstantního ukazatele.  
  
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
  
Pomocí nové knihovny datového proudu `ends` není potřeba, protože řetězec je vždy zakončený hodnotou null, tak, aby řádek můžete odebrat. Pro druhý problém je problém, který teď `str()` nevrací ukazatel na pole znaků pro řetězec; vrátí `std::string` typu. Řešení, aby druhý je typ, který chcete změnit `LPCSTR` a použít `c_str()` metoda požádat o ukazatel.  
  
```cpp  
//*this << ends;  
LPCTSTR psz = str().c_str();    
```  
  
K chybě, která nám puzzled nějakou dobu došlo k chybě pro tento kód.  
  
```cpp  
MOUT << _T(" chUser:'") << chUser  
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');    
```  
  
Makro MOUT přeloží na \*g_pmout, což je objekt typu `mstream`. `mstream` Třída odvozena ze třídy řetězec standardního výstupu `std::basic_ostream<TCHAR>.` ale s _T kolem řetězcový literál, který jsme do v rámci přípravy pro převod do kódu Unicode, rozlišení přetížení pro **operátor <<** nezdaří a zobrazí se následující chybová zpráva:  
  
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
  
Existuje mnoho **operátor <<** definice, že tento druh chyby může být vám nemusí nahánět strach. Po bližším pohledu dostupná přetížení, vidíme, že většina z nich jsou relevantní a vypadající lépe na `mstream` třídy definice, jsme identifikovali následující funkci, která by se v tomto případě by měla být volána.  
  
```cpp  
mstream& operator<<(LPTSTR psz)  
{  
  return (mstream&)ostrstream::operator<<(psz);  
}    
```  
  
Důvod není volána totiž řetězcového literálu má typ `const wchar_t[10]` jak je vidět z poslední řádek dlouhé zobrazila proto převod na ukazatel na nekonstantní není automatické. Ale tento operátor nesmí upravte vstupní parametr, je vhodnější typ parametru `LPCTSTR` (`const char*` při kompilaci jako znakovou sadu MBCS, a `const wchar_t*` jako kódování Unicode), nikoli `LPTSTR` (`char*` při kompilaci jako znaková sada MBCS a `wchar_t*` jako kódování Unicode). Provedení této změny řeší tuto chybu.  
  
Tento typ převodu byla povolena v rámci starší, méně striktní kompilátor ale více poslední změny shody vyžadují více správný kód.  
  
##  <a name="stricter_conversions"></a> Krok 8. Převody přísnější kompilátoru  
 
Máme k dispozici také mnoho chyb vypadat asi takto:  
  
```  
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'  
```  
  
V mapování zprávy, která je jednoduše – makro dojde k chybě:  
  
```cpp  
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)  
// other messages omitted...  
ON_WM_NCHITTEST() // Error occurs on this line.  
END_MESSAGE_MAP()  
```  
  
Přechod na definici toto makro, vidíme, odkazuje na funkci `OnNcHitTest`.  
  
```cpp  
#define ON_WM_NCHITTEST() \  
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \  
(AFX_PMSG)(AFX_PMSGW) \  
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },  
```  
  
Problém souvisí se neshoda v ukazatel na členské funkce typů. Problém není převod z `CHotLinkCtrl` jako typ třídy k `CWnd` jako typ třídy, protože to je platný převod odvozené base. Problém je návratový typ: UINT vs. LRESULT. LRESULT přeloží na LONG_PTR, což je 64bitového ukazatele nebo 32bitového ukazatele, v závislosti na binární typ cíle, UINT nejde převést na tento typ. Toto není, při upgradu kódu napsaného před 2005 od návratového typu mnoho metod mapy zpráv změny z UINT k LRESULT v sadě Visual Studio 2005 jako součást změny 64bitovou kompatibilitou. Můžeme změnit návratový typ z UINT v následujícím kódu na LRESULT:  
  
```cpp  
afx_msg UINT OnNcHitTest(CPoint point);  
```  
  
Po provedení změny máme následující kód:  
  
```cpp  
afx_msg LRESULT OnNcHitTest(CPoint point);  
```  
  
Protože je přibližně deset výskyty této funkce v různé třídy odvozené z CWnd, je vhodné použít **přejít k definici** (klávesnice: **F12**) a **přejít na deklaraci** (Klávesnice: **Ctrl**+**F12**) když ukazatel zůstane na funkci v editoru a najděte tyto a přejděte k nim z **najít Symbol** panel nástrojů. **Přejít k definici** je obvykle další užitečné z nich. **Přejděte do deklarace** bude deklarace najít než definování deklarace, jako je například prohlášení třídy typu friend třídy nebo předávat odkazy.  
  
##  <a name="mfc_changes"></a> Krok 9. Změny knihovny MFC  
 
Další chyba také vztahuje na typ změny deklarace a také dochází v makru.  
  
```Output  
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'  
```  
  
Tento problém je, že druhý parametr `CWnd::OnActivateApp` změnil z HTASK DWORD. Ve verzi Visual Studio, Visual Studio .NET 2002 došlo k této změně.  
  
```cpp  
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);  
```  
  
Musíme aktualizovat deklarace OnActivateApp v odvozených třídách odpovídajícím způsobem následujícím způsobem:  
  
```cpp  
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);  
```  
  
V tuto chvíli nemůžeme ke kompilaci projektu. Existuje několik upozornění pro seznámení se základními, ale a existují volitelné části inovace, jako je například převod ze znakové sady MBCS do kódu Unicode nebo zvýšení zabezpečení pomocí zabezpečení CRT funkce.  
  
##  <a name="compiler_warnings"></a> Krok 10. Vyřešení upozornění kompilátoru  

Pokud chcete získat úplný seznam upozornění, byste měli dělat **sestavit vše znovu** na řešení a nikoli běžné sestavení, pro jistotu této vše, co dříve zkompilován se překompilují, protože dostanete upozornění hlášení jenom z aktuálního kompilace. Další otázkou je, zda se má přijmout aktuální úroveň upozornění nebo používat vyšší úroveň pro upozornění.  Pokud přenášíte velké množství kódu, zejména starý kód, může být vhodné používat vyšší úroveň pro upozornění.  Můžete také chtít začít s výchozí úroveň upozornění a poté zvýšit úroveň pro upozornění zobrazíte všechna upozornění. Pokud používáte `/Wall`, dostanete upozornění v systému souborů záhlaví, použít tolik lidí `/W4` získat maximum upozornění na kód bez zobrazují upozornění pro záhlaví systému. Pokud chcete upozornění jako chyby, přidejte `/WX` možnost. Tato nastavení jsou v **C/C++** část **vlastnosti projektu** dialogové okno.  
  
Jednou z metod v `CSpyApp` třída vyvolá upozornění o funkci, která se už nepodporuje.  
  
```cpp  
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}  
```  
  
Upozornění je následujícím způsobem.  
  
```Output  
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog  
```  
  
Zpráva WM_CTLCOLORDLG byl již zpracovány v kódu nástroje Spy ++, proto byla vyžadována pouze změna odstranit všechny odkazy na `SetDialogBkColor`, které už nepotřebujete.  
  
Další upozornění se snadno vyřešit okomentováním odpovídajícího název proměnné. Dostali jsme následující upozornění:  
  
```Output  
warning C4456: declaration of 'lpszBuffer' hides previous local declaration  
```  
  
Zahrnuje kód, který vytvoří toto makro.  
  
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
  
Použití maker jako tento kód se obvykle učinit kód obtížné udržovat. V takovém případě makra obsahují deklarace proměnné. PARAMETR makra je definovaná následujícím způsobem:  
  
```cpp  
#define PARM(var, type, src)type var = (type)src  
```  
  
Proto `lpszBuffer` získá proměnná deklarovaná dvakrát ve stejné funkci. Není tento straightfoward na tento problém vyřešit, jako kdyby byl, pokud kód nepoužili makra (jednoduše odebrat druhý deklarace typu). Protože se jedná, máme unfortunate volba museli rozhodovat, jestli se má přepsat kódu maker jako běžný kódu (úloha únavné a potenciálně náchylné) nebo zakázat upozornění.  
  
V tomto případě jsme možnost zakázat upozornění. To jde udělat tak, že přidáte pragma následujícím způsobem:  
  
```cpp  
#pragma warning(disable : 4456)  
```  
  
Při zakazování upozornění, můžete chtít omezit zakázat projeví pouze kód, který vytvoří upozornění, aby se zabránilo potlačení upozornění, když ho může poskytují užitečné informace. Můžeme přidat kód pro obnovení upozornění bezprostředně po řádku, která ho vytvořila, nebo ještě lepší, protože toto varování se objeví v makru, použít **__pragma** – klíčové slovo, které funguje v makrech (`#pragma` nefunguje v makrech).  
  
```cpp  
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \  
type var = (type)src \  
__pragma(warning(default : 4456))    
```  
  
Další upozornění vyžaduje některé revize kódu. Rozhraní API systému Win32 `GetVersion` (a `GetVersionEx`) je zastaralý.  
  
```Output  
warning C4996: 'GetVersion': was declared deprecated  
```  
  
Následující kód ukazuje, jak získat verzi.  
  
```cpp  
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.  
DWORD dwWindowsVersion = GetVersion();    
```  
  
To je následována velké množství kódu, který prověří dwWindowsVersion hodnotu, která určí, zda máme spuštěnou na Windows 95 a kterou verzi systému Windows NT. Protože se jedná všechny zastaralé, můžeme odebrat kód a řešit všechny odkazy na tyto proměnné.  
  
Tento článek [změny verze operačního systému ve Windows 8.1 a Windows Server 2012 R2](https://msdn.microsoft.com/library/windows/desktop/dn302074.aspx) vysvětluje situace.  
  
Metody v `CSpyApp` třídu, která se dotazovat na verzi operačního systému: `IsWindows9x`, `IsWindows4x`, a `IsWindows5x`. Dobrým výchozím bodem je předpokládat, že verze Windows, který plánujeme podporu (Windows 7 a novější) jsou všechny zavřít, že jde o 5 Windows NT jako úplně technologie používané v této starší aplikace. Používá tyto metody se vypořádat s omezeními starší operační systémy. Proto jsme změnili tyto metody, vrátí hodnotu TRUE pro `IsWindows5x` a hodnotu FALSE pro ostatní.  
  
```cpp  
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }  
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }  
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }    
```  
  
Který zbývá jen na několika místech, kde byly vnitřních proměnných použít přímo. Protože jsme odebrali těchto proměnných, získáme několik chyb, které musí řešit explicitně.  
  
```Output  
error C2065: 'm_bIsWindows9x': undeclared identifier  
```  
  
```cpp  
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)  
{  
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);  
}    
```  
  
Jsme může nahraďte volání metody nebo jednoduše předejte hodnotu TRUE a odeberte staré zvláštní případ pro Windows 9 x.  
  
```cpp  
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)  
{  
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);  
}    
```  
  
Poslední upozornění na výchozí úrovni (3) souvisí se bitového pole.  
  
```Output  
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0  
```  
  
Kód, který aktivuje to vypadá takto.  
  
```cpp  
m_bStdMouse = TRUE;  
```  
  
Deklarace `m_bStdMouse` označuje, že se jedná bitového pole.  
  
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
  
Tento kód byl zapsán před integrované logický typ je podporován v jazyce Visual C++. Takový kód, BOOL úspěšně jste se **typedef** pro **int**. Typ **int** je **podepsané** typu a bitové reprezentace **znaménkem** je použít první bit jako bit znaménka tak bitového pole typu int, může být interpretován jako 0 nebo -1, které pravděpodobně není co byl určen.  
  
Byste vlastně nevěděli o pohledem na kód proto jde o bitová pole. Záměr udržet co nejmenší velikost objektu, nebo existuje je kdekoli ve kterém se používá binární rozložení objektu? Jsme změnili tyto běžné členy BOOL, protože jsme nezobrazila z jakéhokoli důvodu pro použití bitového pole. Použití bitová pole, která udržuje velikost objektu malé nemusí fungovat. To závisí na tom, jak kompilátor rozložen typ.  
  
Může vás zajímat, pokud používáte standardní typ **bool** v rámci by mohl být užitečný. Mnohé z původní kód vzory, třeba typ BOOL byly vymyšlený k řešení problémů, které byly vyřešeny později ve standardním jazyce C++, takže změna z typu BOOL na **bool** předdefinovaný typ je pouze jeden příklad takové změny vezměte v úvahu to za vás odeslání kódu na začátku spuštění v nové verzi.  
  
Jakmile jsme jste řešeny všechna upozornění, které se zobrazí na výchozí úrovni (úroveň 3) jsme změnili na úrovně 4 pro zachycení několika dalších upozornění. První, kdo se zobrazí se takto:  
  
```Output  
warning C4100: 'nTab': unreferenced formal parameter  
```  
  
Kód, který vytváří tato upozornění byla následujícím způsobem.  
  
```cpp  
virtual void OnSelectTab(int nTab) {};  
```  
  
Vypadá to, že dostatečně neškodné, ale od té doby jsme chtěli čisté kompilace s `/W4` a `/WX` nastavit, můžeme jednoduše označené jako komentář název proměnné, se v něm pro účely čitelnosti.  
  
```cpp  
virtual void OnSelectTab(int /*nTab*/) {};  
```  
  
Další varování, které jsme obdrželi byly užitečné pro vyčištění obecné kódu. Existuje mnoho implicitní převody z **int** nebo **unsigned int** do aplikace WORD (což je definice typu **unsigned short**). Ty zahrnují může dojít ke ztrátě dat. Přidali jsme přetypování do aplikace WORD v těchto případech.  
  
Další upozornění úrovně 4, které nám dává pro tento kód byl:  
  
```Output  
warning C4211: nonstandard extension used: redefined extern to static  
```  
  
Tento problém nastane, pokud nejprve proměnná byla deklarovaná **extern**, později deklarované **statické**. Se vzájemně vylučují význam tyto dva specifikátory třídy úložiště, ale je to povoleno jako rozšíření společnosti Microsoft. Pokud chcete získat kód pro jeho přenositelnost na jiné kompilátory, nebo si přejete kompilovat s `/Za` (Kompatibilita s ANSI), by změnit deklarace mít odpovídající specifikátory třídy úložiště.  
  
##  <a name="porting_to_unicode"></a> Krok 11. Portování ze znakové sady MBCS do kódu Unicode

Všimněte si, že na světě Windows, když říkáme kódování Unicode, obvykle myslíme UTF-16. Jiné operační systémy, jako je Linux používat kódování UTF-8, ale Windows obecně neuvádí. Verze MBCS MFC se přestala nabízet v sadě Visual Studio 2013 a 2015, ale již není již v sadě Visual Studio 2017. Pokud používáte Visual Studio 2013 nebo 2015, před provedením kroku k opravdu portu znakové sady MBCS kódu Unicode UTF-16, chceme může dočasně eliminovat upozornění, že se již nepoužívá znakové sady MBCS, aby bylo možné provádět další operace nebo odložit přenesení do vhodnou dobu. Aktuální kód používá znakovou sadu MBCS a chcete-li pokračovat, potřebujeme nainstalovat verzi ANSI/znakové sady MBCS MFC. Docela rozsáhlá knihovna MFC není součástí výchozí sady Visual Studio **vývoj desktopových aplikací pomocí C++** instalace, takže musí být vybrán z volitelné součásti v instalačním programu. Zobrazit [MFC MBCS DLL – doplněk](../mfc/mfc-mbcs-dll-add-on.md). Jakmile stáhněte si tuto aplikaci a restartujte aplikaci Visual Studio, můžete zkompilovat a propojit s verzí znakové sady MBCS MFC, ale se jich zbavit varování o znakové sady MBCS, pokud používáte Visual Studio 2013 nebo 2015, měli byste také přidat NO_WARN_MBCS_MFC_DEPRECATION do vašeho seznamu předdefinovaných makra v **preprocesor** části Vlastnosti projektu, nebo na začátku souboru stdafx.h záhlaví nebo jiných společný soubor hlaviček.  
  
Nyní je k dispozici některé chyby linkeru.  
  
```Output  
fatal error LNK1181: cannot open input file 'mfc42d.lib'  
```  
  
LNK1181 dochází, protože obsahuje zastaralý statickou knihovnu verzi knihovny mfc linker input. Není to povinné zobrazovat, protože jsme dynamicky propojí knihovnu MFC, potřebujeme jenom odebrat všechny statické knihovny MFC z **vstup** vlastnost **Linkeru** části Vlastnosti projektu. Tento projekt používá také `/NODEFAULTLIB` možnost, a místo toho vypíše všechny závislosti knihoven.  
  
```  
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)  
```  
  
Teď nám skutečně aktualizujte starý kód vícebajtové znakové sady (MBCS) do kódování Unicode. Protože jde o aplikaci Windows, úzce vázané na desktopové platformy Windows, jsme se port na Unicode UTF-16, který používá Windows. Při psaní kódu napříč platformami nebo přenesení aplikací Windows pro jiné platformy, můžete chtít zvážit přenos na UTF-8, který je běžně používaný v jiných operačních systémech.  
  
Portování do Unicode UTF-16, jsme musíte rozhodnout, zda stále chceme možnost kompilace do znakové sady MBCS, nebo ne.  Pokud chcete mít možnost pro podporu znakové sady MBCS, bychom měli použít makra TCHAR jako typ znaku, který se přeloží na buď **char** nebo **wchar_t**, v závislosti na tom, zda je definován _MBCS nebo _UNICODE během kompilace. Přepnutí do Tchar – a TCHAR verzích různá rozhraní API namísto **wchar_t** a jeho přidružené rozhraní API znamená, že můžete vrátit na verzi znakové sady MBCS kódu jednoduše tak, že definice makra _MBCS místo _UNICODE. Kromě TCHAR existuje širokou škálu TCHAR verze jako je často používaný – definice TypeDef, makra a funkce. Například LPCTSTR místo LPCSTR a tak dále. V dialogovém okně Vlastnosti projektu v části **vlastnosti konfigurace**v **Obecné** oddíl, změna **znaková sada** vlastnost z **pomocí znakové sady MBCS Znaková sada** k **použít znakovou sadu Unicode**. Toto nastavení má vliv, které – makro je předdefinovaná během kompilace. Je UNICODE makra a makra _UNICODE. Vlastnost projektu ovlivňuje konzistentně. Záhlaví Windows používat kódování UNICODE, kde _UNICODE použít záhlaví Visual C++, jako je například knihovny MFC, ale v případě, že je definován, druhá je vždy definována.  
  
Vhodná [průvodce](http://msdn.microsoft.com/library/cc194801.aspx) pomocí TCHAR existuje pro přenos ze znakové sady MBCS do kódu Unicode UTF-16. Můžeme vybrat tuto trasu. Nejprve Změníme **znaková sada** vlastnost **pomocí Unicode znaková sada** a sestavte projekt znovu.  
  
Některá místa v kódu už používali TCHAR, zjevně čekat na případná nakonec podporu kódování Unicode. Některé nebyly. Jsme hledali výskyty ZNAKU, který je **– typedef** pro **char**a nahradí TCHAR většina z nich. Kromě toho jsme hledán `sizeof(CHAR)`. Pokaždé, když jsme změnili z CHAR TCHAR, jsme obvykle měli změnit na `sizeof(TCHAR)` vzhledem k tomu, že to se často používá k určení počtu znaků v řetězci. Pomocí nesprávného typu tady nevytváří chybu kompilátoru, proto je vhodné platit hodně pozornost tento případ.  
  
Tohoto typu chyby je velmi běžné bezprostředně po přepnutí do kódu Unicode.  
  
```Output  
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'  
```  
  
Tady je příklad kódu, který vytvoří toto:  
  
```cpp  
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);  
```  
  
Máme _T kolem řetězec literálu odebrat chyby.  
  
```cpp  
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);  
```  
  
_T – makro má vliv na provádění řetězec literálu kompilovat jako **char** řetězec nebo **wchar_t** řetězec, v závislosti na nastavení znakové sady MBCS a UNICODE. Chcete-li nahradit všechny řetězce _T v sadě Visual Studio, nejprve otevřete **rychlého nahrazení** (klávesnice: **Ctrl**+**F**) pole nebo **nahrazování v souborech**  (Klávesnice: **Ctrl**+**Shift**+**H**), klikněte na tlačítko **použijte regulární Výrazy** zaškrtávací políčko. Zadejte `((\".*?\")|('.+?'))` jako hledaný text a `_T($1)` jako náhradní text. Pokud už máte _T – makro kolem některé řetězce, tento postup přidá ho znovu a setkat i případy, kdy nechcete _T, jako je například při použití `#include`, takže je vhodné použít **nahradit další** spíše než  **Nahradit vše**.  
  
 Tato funkce [wsprintf](/windows/desktop/api/winuser/nf-winuser-wsprintfa), je ve skutečnosti definovány v záhlaví Windows a v dokumentaci pro doporučí, že se nepoužívají, z důvodu přetečení vyrovnávací paměti je to možné. Není uvedena velikost pro `szTmp` vyrovnávací paměti, takže neexistuje žádný způsob, jak funkce, zkontrolujte, že vyrovnávací paměti může obsahovat všechna data, která má být zapsán do něj. Viz následující část o převodu na zabezpečení CRT, ve kterém jsme podobnými problémy opravit. Jsme skončila jeho nahrazením [_stprintf_s –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).  
  
Další běžnou chybou, který se zobrazí při převodu do kódování Unicode je to.  
  
```Output  
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'  
```  
  
Kód, který ho vytvořila vypadá takto:  
  
```cpp  
pParentNode->m_szText = new char[strTitle.GetLength() + 1];  
_tcscpy(pParentNode->m_szText, strTitle);  
```  
  
I když `_tcscpy` funkce byla použita, což je TCHAR strcpy – funkce pro kopírování řetězce, vyrovnávací paměť, která byla přidělena byla **char** vyrovnávací paměti. Snadno se změní na TCHAR.  
  
```cpp  
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];  
_tcscpy(pParentNode->m_szText, strTitle);    
```  
  
Podobně změnili jsme LPSTR (dlouhým ukazatelem na řetězec) a LPCSTR (dlouhým ukazatelem s konstantním řetězcem) LPTSTR (dlouhým ukazatelem na řetězec TCHAR) a LPCTSTR (dlouhým ukazatelem na konstanty typu řetězec TCHAR), když garantována chybu kompilátoru. Zvolili jsme Nedělejte nahrazení pomocí globálního hledání a nahrazení, protože obě situace museli posuzují jednotlivě. V některých případech **char** chtěla verze, například při zpracování některých Windows zpráv, která může použít Windows struktury, které mají **A** příponu. V rozhraní Windows API, přípona **A** znamená, že ASCII a ANSI (a také vztahuje na znakové sady MBCS) a přípony **W** znamená, že široké znaky nebo Unicode UTF-16. Tento vzorec pojmenování se používá v hlavičkách Windows, ale jsme také a potom ho v kódu nástroje Spy ++ při museli jsme přidat Unicode verze funkce, která již byla definována v pouze verzi znakové sady MBCS.  
  
V některých případech jsme museli nahradit typ má být použit na verzi, která řeší správně (WNDCLASS místo WNDCLASSA příkladu).  
  
V řadě případů jsme museli používat obecná verzi (makro) rozhraní Win32 API, jako je `GetClassName` (místo `GetClassNameA`). V příkazu switch obslužné rutiny zpráv, některé zprávy jsou specifické pro znakovou sadu MBCS a Unicode, v těchto případech, abychom museli kód explicitně volat verzi znakové sady MBCS, změnit, protože jsme obecně pojmenované funkce se nahradí **A** a **W** specifické funkce a přidá makro pro obecný název, který se překládá na správný **A** nebo **W** název založený na tom, jestli je definována kódování UNICODE.  V mnoha části kódu, když jsme přešli k definování _UNICODE, W verze je teď zvolené i v případě **A** verze není co chtěli.  
  
Nejsou k dispozici na několika místech, kde musel být přijata zvláštní akce. Jakékoli použití `WideCharToMultiByte` nebo `MultiByteToWideChar` může vyžadovat podívat podrobněji. Tady je jeden příklad kde `WideCharToMultiByte` se používal.  
  
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
  
Proto jsme měli pochopit, že důvodem k tomu bylo potřeba zkopírovat řetězec širokého znaku představující název písma do vnitřní vyrovnávací paměť `CString`, `strFace`. To vyžaduje mírně odlišný kód pro vícebajtové `CString` řetězců jako širokého znaku `CString` řetězce, proto jsme přidali `#ifdef` v tomto případě.  
  
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
  
Samozřejmě, nikoli z `wcscpy` jsme skutečně používejte `wcscpy_s`, bezpečnější verze. Další část se věnuje toto.  
  
Ke kontrole na práci jsme měli obnovit **znaková sada** k **použití vícebajtové znakové sady** a ujistěte se, že kód stále zkompiluje, pomocí znakové sady MBCS a Unicode. Needless znamená pass celý test by měl provést u rekompilované aplikace po provedení těchto změn.  
  
V naší práci s tímto řešením nástroje Spy ++, jakou trvalo asi dvou pracovních dnů pro vývojáře průměrné C++ k převodu kódu Unicode. Který neobsahuje retesting čas.  
  
##  <a name="porting_to_secure_crt"></a> Krok 12. Portování do použijte zabezpečení CRT  
 
Portování kódu použít bezpečné verze (verze s **_Malá** přípona) CRT funkce je další. V tomto případě je obecná strategie pro nahrazení funkce s **_Malá** verzi a poté obvykle, přidejte parametry velikost požadované vyrovnávací paměti další. V mnoha případech jde jednoduché vzhledem k tomu, že se označuje velikost. V ostatních případech, kde velikost není okamžitě k dispozici, je potřeba přidat další parametry pro funkci, která používá funkce CRT, nebo možná prozkoumat využití vyrovnávací paměti cílového a naleznete v tématu co odpovídající velikost mezní hodnoty.  
  
Trik, aby bylo snazší získat kód zabezpečení bez přidání parametrů velikost poskytuje jazyk Visual C++, a to je pomocí přetížení šablon. Protože tato přetížení šablon, jejich jsou dostupné jenom při kompilaci jako C++, nepřináší C. Spyxxhk je projekt C tak zdvih nebude fungovat, který.  Ale není Spyxx a používáme zdvih. Trik, jak zajistit, je na místě, kde ji se zkompiluje do každého souboru projektu, například v souboru stdafx.h přidejte řádek podobný následujícímu:  
  
```cpp  
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1  
```  
  
Když definujete, pokaždé, když je pole vyrovnávací paměť, místo nezpracovaný ukazatel, jeho velikost je odvozen z typu pole a, který se používá jako parametr velikosti, aniž byste museli zadávat. Která pomáhá omezit složitost přepisování kódu. Stále je nutné nahradit název funkce **_Malá** verze, ale často to provést pomocí vyhledávání a nahrazení operace.  
  
Návratové hodnoty některé funkce změnit. Například `_itoa_s` (a `_itow_s` a makra `_itot_s`) vrátí kód chyby (`errno_t`), namísto řetězce. Takže v těchto případech budete muset přesunout volání `_itoa_s` na samostatném řádku a nahraďte ji metodou identifikátor přípravné vyrovnávací paměti.  
  
Některé běžné příklady: pro `memcpy`, při přechodu k `memcpy_s`, přidali jsme často velikost struktury je zkopírován do. Podobně pro většinu řetězce a vyrovnávací paměti, velikost pole nebo vyrovnávací paměti se snadno určuje od deklarace vyrovnávací paměti nebo hledáním, kde byla původně přidělené vyrovnávací paměti. V některých situacích je potřeba určit, jak velký objem vyrovnávací paměti je ve skutečnosti k dispozici, a pokud tyto informace není k dispozici v oboru funkce, který modifikujte, by měl být přidán jako další parametr a volající kód by měl být upraven na Zadejte informace.  
  
Pomocí následujících postupů, jakou trvalo přibližně půl za den pro převod kód, který použije zabezpečené funkce CRT. Pokud jste vybrali možnost přetížení šablon a ručně přidejte parametry velikosti, by pravděpodobně využijte dvakrát nebo třikrát déle.  
  
##  <a name="deprecated_forscope"></a> Kroku 13. /Zc:forScope-je zastaralý.  
 
Od verze Visual C++ 6.0 kompilátor odpovídá aktuální standardu, který omezuje obor proměnné deklarované ve smyčce do oboru smyčky. Možnost kompilátoru [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**vynutit dodržování standardu pro obor cyklu for** ve vlastnostech projektu) určuje, zda bude ohlášena za chybu. Aktualizujeme by měl náš kód, aby splňovala podmínky shody a přidejte deklarace pouze mimo smyčku. Pro vyvarování změn kódu, můžete změnit nastavení **jazyk** části Vlastnosti projektu C++ k `No (/Zc:forScope-)`. Nicméně, mějte na paměti, která `/Zc:forScope-` v budoucí verzi jazyka Visual C++, takže nakonec bude nutné změnit tak, aby odpovídal standardu váš kód může být odstraněna.  
  
Tyto problémy jsou relativně snadno to vyřešíme, ale v závislosti na vašem kódu, může to ovlivnit velké množství kódu. Zde je typický problém.  
  
```cpp  
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const  
{  
  for (int n = 0; mszStrings[0] != 0; n++)  
  mszStrings = _tcschr(mszStrings, 0) + 1;  
  return(n);  
}    
```  
  
Výše uvedený kód vygeneruje chybu:  
  
```Output  
'n': undeclared identifier  
```  
  
K tomu dochází, protože kompilátor se nepoužívá možnost kompilátoru, která kód, který již splňuje C++ standard. Ve standardu deklarace proměnné uvnitř smyčka omezuje jeho rozsah smyčky, takže běžnou praxí pomocí čítače cyklů mimo smyčku vyžaduje, aby deklarace čítač také přesunout mimo smyčku, stejně jako v následujícím upravený kód :  
  
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
 
Portování nástroje Spy ++ od původního kódu Visual C++ 6.0 na nejnovější kompilátor trvalo asi 20 hodin kódování o týden v průběhu času. Budeme upgradovat přímo přes osm verzemi produktu Visual Studio 6.0 na Visual Studio 2015. Teď je to doporučený postup pro všechny upgrady na projektech malé i velké.  
  
## <a name="see-also"></a>Viz také  

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)   
[Předchozí Případová studie: COM Spy](../porting/porting-guide-com-spy.md)