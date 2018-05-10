---
title: 'Průvodce přenosem: Spy ++ | Microsoft Docs'
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
ms.openlocfilehash: f645d1202149ae2625d5a15df5be61029beb6ab1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="porting-guide-spy"></a>Průvodce přenosem: Spy++
Tato přenosem Případová studie slouží k získáte představu o jaké typické přenosem projekt je stejně jako typy problémů, může dojít k a některé obecné tipy a triky pro adresování přenosem problémy. Smyslem není jako spolehlivý Průvodce přenosem, protože možností portování projektu velmi mnohem závisí na specifika kódu.  
  
## <a name="spy"></a>Spy++  
 Nástroje Spy ++ je často používaný diagnostický nástroj grafického uživatelského rozhraní pro plochu Windows, která poskytuje všem druhům informací o prvky uživatelského rozhraní na ploše systému Windows. Zobrazuje úplný hierarchii systému windows a poskytuje přístup k metadatům o každé okno a řízení. Tuto aplikaci užitečné má dodávané pomocí sady Visual Studio pro mnoho let. Zjistili jsme, stará verze to, který byl naposledy zkompilovat ve Visual C++ verze 6.0 a přesně do sady Visual Studio 2015. Prostředí pro Visual Studio 2017 by měl být téměř shodné.
  
 Jsme považován za tento případ typická pro přenos aplikací klasické pracovní plochy Windows využívající rozhraní MFC a rozhraní API Win32 hlavně pro původní projekty, které nebyly aktualizovány při každém vydání Visual C++ od Visual C++ verze 6.0.  
  
##  <a name="convert_project_file"></a> Krok 1. Převádění souboru projektu.  
 Soubor projektu, dvě staré .dsw soubory z Visual C++ verze 6.0, převést snadno bez problémů, které vyžadují další pozornost. Aplikace nástroje Spy ++ je jeden projekt. Druhá je SpyHk, které jsou napsané v jazyce C, podpůrné knihovny DLL. Složitější projekty nemusí upgradovat snadno, jak je popsáno [zde](../porting/visual-cpp-porting-and-upgrading-guide.md).  
  
 Po dokončení upgradu dva projekty naše řešení hledá takto:  
  
 ![Nástroji Spy&#43; &#43; řešení](../porting/media/spyxxsolution.PNG "SpyxxSolution")  
  
 Máme dva projekty, jeden s velkým počtem C++ soubory a jiné knihovny DLL, která je napsána v C.  
  
##  <a name="header_file_problems"></a> Krok 2. Záhlaví souboru problémy  
 Při sestavování nově převedený projekt, jedním z nejdůležitějších věcí, které budete často zjistíte je, že nebyly nalezeny soubory hlaviček, které používá váš projekt.  
  
 Byl jeden ze souborů, které se nenašel v nástroji Spy ++ verstamp.h. Z hledání v Internetu jsme určili, to pochází DAO SDK, technologie zastaralá data. Jsme chtěli zjistit, jaké symboly byly používá z hlavičkový soubor, pokud byl tento soubor skutečně potřeba, nebo zda tyto symboly nebyly definované jinam, takže jsme označeno jako komentář deklaraci hlavičky souboru a překompilovat. Stane se z odhlašování došlo je jen jeden symbol, který je potřeba, VER_FILEFLAGSMASK.  
  
```  
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK  
```  
  
 Nejjednodušší způsob, jak najít v souborech k dispozici zahrnout symbol je používání funkce najít v souborech (Ctrl + Shift + F) a zadejte **adresáře Include Visual C++**. Jsme našli v ntverp.h. Jsme nahradit verstamp.h zahrnout ntverp.h a tato chyba není dostupné.  
  
##  <a name="linker_output_settings"></a> Krok 3. Nastavení výstupní soubor linkeru  
 Starší projekty někdy nutné soubory umístěné v neobvyklé umístění, které mohou způsobovat problémy po upgradu. V takovém případě máme $(solutiondir) – přidejte do cesty k zahrnutí ve vlastnostech projektu zajistit, že Visual Studio můžete najít některé soubory hlavičky, které jsou umístěny existuje, a nikoli v jednom ze složky projektu.  
  
 MSBuild complains, že vlastnost Link.OutputFile neodpovídá hodnoty TargetPath a TargetName vystavování MSB8012.  
  
```Output  
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).  
```  
  
 **Link.OutputFile** je výstup sestavení (EXE, DLL, např.) a je obvykle vytvářejí na základě $(TargetDir)$(TargetName)$(TargetExt), udělíte cesta, název souboru a rozšíření. Toto je běžnou chybou při migraci projekty z původního Visual C++ sestavení nástroj (vcbuild.exe) do nového nástroje sestavení (MSBuild.exe). Vzhledem k tomu, že v sadě Visual Studio 2010 došlo ke změně nástroj pro sestavení, může dojít, tento problém vždy, když migrujete projektu Project 2010 2010 nebo novější verze. Základní problém je, že Průvodce migrací projektu neaktualizuje **Link.OutputFile** hodnotu vzhledem k tomu, že vždy není možné určit, co by měl mít hodnotu na základě jiných nastavení projektu. Proto je obvykle nutné nastavit ručně. Další podrobnosti najdete v tématu to [post](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) na blogu Visual C++.  
  
 V takovém případě **Link.OutputFile** v převedený projektu byla nastavena na.\Debug\Spyxx.exe a.\Release\Spyxx.exe nástroje Spy ++ projektu, v závislosti na konfiguraci. Nejvhodnější dokument je jednoduše nahradit tyto hodnoty pevně zakódované $(TargetDir)$(TargetName)$(TargetExt) u všech konfigurací. Pokud to nefunguje, můžete přizpůsobit odtud nebo změny vlastností v části Obecné, kde jsou tyto hodnoty nastavené (vlastnosti jsou **výstupního adresáře**, **cílová**, a  **Cíl rozšíření**. Mějte na paměti, že pokud vlastnost prohlížíte používá makra, můžete zvolit **upravit** v rozevíracím seznamu se zprovoznit dialogové okno se zobrazuje posledním řetězci s provedeny náhrady makro. Všechny dostupné makra a jejich aktuální hodnoty můžete zobrazit výběrem **makra** tlačítko.  
  
##  <a name="updating_winver"></a> Krok 4. Aktualizace na cílovou verzi systému Windows  
 Další chyba označuje, že WINVER verzi není podporován v prostředí MFC. WINVER pro systém Windows XP je 0x0501.  
  
```Output  
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.  
```  
  
 Windows XP je podporován společností Microsoft, takže i když ho cílení je povolena v sadě Visual Studio 2015, by měl být postupné omezení podpory pro něj ve svých aplikacích a podporou uživatelům použít nové verze systému Windows.  
  
 Chcete-li odstranit chyby, definovat WINVER aktualizací **vlastnosti projektu** nastavení na nejnižší verze systému Windows, které jsou aktuálně chcete cílit. Najít tabulku hodnot pro různé verze Windows [zde](http://msdn.microsoft.com/library/windows/desktop/aa383745.aspx).  
  
 Soubor stdafx.h obsahoval některé z těchto definice maker.  
  
```cpp  
#define WINVER       0x0500  // these defines are set so that we get the  
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,  
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.  
  
```  
  
 WINVER se nastaví na systém Windows 7. Je snadnější čtení kód později Pokud používáte makro pro systém Windows 7 (_WIN32_WINNT_WIN7), nikoli hodnotu samotnou (0x0601).  
  
```cpp  
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7  
```  
  
##  <a name="linker_errors"></a> Krok 5. Chybami linkeru  
 Tyto změny sestavení projektu SpyHk (DLL) ale způsobí chybu linkeru.  
  
```  
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12  
```  
  
 Vstupní bod pro knihovny DLL nesmí exportovat. Vstupní bod je určena pouze k volání zavaděčem při knihovnu DLL prvním načtení do paměti, takže by nemělo být v tabulce exportu, což je pro ostatní volající. Potřebujeme zajistit nemá `__declspec(dllexport)` – direktiva k němu připojen. V spyxxhk.c budeme muset odebrat ze dvou míst, deklarace a definice DLLEntryPoint. Nikdy byly provedeny se použije tato direktiva, ale předchozí verze kompilátoru a linkeru není příznak jako problém. V novějších verzích linkeru poskytnout upozornění.  
  
```cpp  
// deleted __declspec(dllexport)  
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);  
  
```  
  
 Projekt C DLL, SpyHK.dll, teď sestavení a propojuje bez chyby.  
  
##  <a name="outdated_header_files"></a> Krok 6. Více zastaralé soubory hlaviček  
 V tuto chvíli jsme začátek práce na hlavní spustitelný projekt, Spyxx.  
  
 Nebyl nalezen pár dalších zahrnout soubory: ctl3d.h a penwin.h. Může být užitečné pro vyhledávání v Internetu a pokouší se určit, co zahrnuté záhlaví, někdy informace není to užitečné. Zjistili jsme, ctl3d.h se součást Exchange Development Kit a poskytuje podporu pro určité styl ovládacích prvků v systému Windows 95, a penwin.h má vztah k okno pera Computing zastaralá rozhraní API. V takovém případě můžeme jednoduše komentář #include řádek a řešit nedefinované symboly, jako jsme to udělali s verstamp.h. Všechno, co se má vztah k 3D ovládací prvky nebo pera Computing byla odebrána z projektu.  
  
 Vzhledem k projektu s mnoha kompilace chyb, které jsou postupně odstraňuje, není realistické najít všechny používá zastaralá rozhraní API hned, když odeberete #include – direktiva. Jsme nebyla zjišťovat okamžitě, ale spíše na některé pozdější místo byla přijata chyba, WM_DLGBORDER nebyla definována. Ve skutečnosti pouze jeden, je mnoho nedefinované symboly, které pocházejí z ctl3d.h. Jakmile jste jsme určili, že má vztah k rozhraní API zastaralé, jsme odebrali všechny odkazy v kódu na ni.  
  
##  <a name="updating_iostreams_code"></a> Krok 7. Aktualizace staré iostreams kódu  
 Další chyba je běžné s původním C++ kód, který používá iostreams.  
  
 mstream.h(40): závažná chyba C1083: Nelze otevřít vložený soubor: 'iostream.h': podobný soubor nebo adresář  
  
 Problém je, že má staré knihovny iostreams odebrat a nahradit. Máme nahraďte staré iostreams novější standardy.  
  
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
  
 Díky této změně máme problémy s ostrstream, který se už používá. Odpovídající nahrazení je ostringstream –. Pokusíme přidání typedef pro ostrstream, aby se zabránilo změny kódu příliš mnoho alespoň jako spuštění.  
  
```cpp  
typedef std::basic_ostringstream<TCHAR> ostrstream;  
  
```  
  
 Aktuálně projektu je sestaven pomocí znakové sady MBCS (vícebajtový znaková sada), takže `char` je datový typ odpovídající znaku. Ale povolit jednodušší aktualizace kód na kódování Unicode UTF-16, budeme aktualizovat na `TCHAR`, který přeloží na `char` nebo `wchar_t` podle toho, jestli **znaková sada** v nastavení projektu je nastavena na Znakové sady MBCS nebo Unicode.  
  
 Několik dalších částí kódu je nutné aktualizovat.  Ios_base – bylo nahrazeno ios základní třídy a jsme nahrazený ostream – je basic_ostream\<T >. Přidáme dva další definice TypeDef a zkompiluje v této části.  
  
```cpp  
typedef std::basic_ostream<TCHAR> ostream;  
typedef ios_base ios;  
  
```  
  
 Pomocí těchto – definice TypeDef je pouze dočasné řešení. Pro více trvalé řešení budeme může aktualizovat každý odkaz na rozhraní API přejmenován nebo zastaralá.  
  
 Zde je další chyby.  
  
```Output  
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'  
```  
  
 Další problém je, že tento basic_stringbuf nemá metoda ukotvit. Aby se zabránilo nevrácenou pamětí v původním ostream – se používá metoda ukotvit. Teď, když používáme nové ostringstream – jsme není nutné ho. Jsme můžete odstranit volání ukotvit.  
  
```cpp  
//rdbuf()->freeze(0);  
```  
  
 Sousední řádků došlo k následující dva chybám. První complains o používání zakončení, což je manipulator staré knihovny iostream vstupně-výstupní operace, která přidává zakončením hodnotu null na řetězec.  Druhý tyto chyby vysvětluje, že výstup str – metoda nemůže být přiřazen jiný const ukazatel.  
  
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
  
 Pomocí nové knihovny datového proudu, není potřeba končí, vzhledem k tomu, že řetězec má vždy ukončené hodnotou null, tak, aby řádku lze odebrat. Pro druhý problém problém je, že teď str() nevrací ukazatele na pole znaků řetězce; Vrátí typ std::string. Řešení, aby druhý je změnit typ na LPCSTR a použít metodu c_str() k žádosti o ukazatele.  
  
```cpp  
//*this << ends;  
LPCTSTR psz = str().c_str();  
  
```  
  
 K chybě, která nám puzzled nějakou dobu došlo k chybě na tento kód.  
  
```cpp  
MOUT << _T(" chUser:'") << chUser  
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');  
  
```  
  
 Makro `MOUT` přeloží na * g_pmout, což je objekt typu `mstream`. Třída mstream je odvozena od třídy řetězec standardní výstup `std::basic_ostream<TCHAR>.` ale s _T kolem řetězcový literál, který jsme chápat v rámci přípravy pro převod na kódování Unicode, rozlišení přetížení operátoru << selže s následující chybou zpráva:  
  
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
  
 Existuje mnoho operátor << definice, že tento druh chyby mohou být první pohled poněkud složité. Po přesněji prohlížení k dispozici přetížení, uvidíte, že většina z nich jsou důležité a vypadající přesněji na `mstream` třídy definice myslíme, že následující funkce, které Věříme, že by měla být volána v tomto případě.  
  
```cpp  
mstream& operator<<(LPTSTR psz)  
{  
  return (mstream&)ostrstream::operator<<(psz);  
}  
  
```  
  
 Z důvodu není volán totiž řetězcový literál má typ `const wchar_t[10]` jak vidíte z poslední řádek tohoto dlouho chybová zpráva, takže převod na jiný const ukazatel není automatické. Tento operátor ale neměli upravovat vstupní parametr, tak, aby lépe odpovídající typ parametru LPCTSTR (`const char*` při kompilaci jako MBCS, a `const wchar_t*` jako Unicode), není LPTSTR (`char*` při kompilaci jako MBCS, a `wchar_t*` jako Unicode). Provedení této změny opravy této chyby.  
  
 Tento typ převodu byla povolena v kompilátoru starší, méně přísná, ale novější shoda změny vyžadují více správný kód.  
  
##  <a name="stricter_conversions"></a> Krok 8. Převody více striktní kompilátoru  
 Můžeme také získat mnoho chyb takto:  
  
```  
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'  
```  
  
 V mapy zpráv, který je jednoduše makro dojde k chybě:  
  
```cpp  
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)  
// other messages omitted...  
ON_WM_NCHITTEST() // Error occurs on this line.  
END_MESSAGE_MAP()  
```  
  
 Přejít k definici této makro, vidíte, že odkazuje na funkci OnNcHitTest.  
  
```cpp  
#define ON_WM_NCHITTEST() \  
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \  
(AFX_PMSG)(AFX_PMSGW) \  
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },  
```  
  
 Tento problém souvisí se neshoda v má ukazatel na funkci typy členů. Vzhledem k tomu, který je platný převod odvozené základní, není problém převod CHotLinkCtrl jako typ třídy CWnd jako typ třídy. Problém je návratový typ: Celé_číslo vs. LRESULT. LRESULT přeloží na LONG_PTR, což je ukazatel 64-bit nebo ukazatel 32-bit, v závislosti na binární typ cíle, takže Celé_číslo nepřevede k tomuto typu. To je běžné při upgradu kód napsaný před 2005 vzhledem k tomu, že návratový typ mnoho metody map zpráv změněn z Celé_číslo na LRESULT v sadě Visual Studio 2005 jako součást změny 64-bit kompatibility. Nemůžeme změnit návratový typ z Celé_číslo v následujícím kódu na LRESULT:  
  
```cpp  
afx_msg UINT OnNcHitTest(CPoint point);  
```  
  
 Po provedení změny máme následující kód:  
  
```cpp  
afx_msg LRESULT OnNcHitTest(CPoint point);  
```  
  
 Vzhledem k tomu, že jsou přibližně deset výskyty této funkce ve různé třídy odvozené od CWnd, je vhodné použít **přechod na definici** (klávesové: F12) a **přejít na deklaraci** (klávesové: Ctrl + F12) při kurzor je na funkci v editoru a najděte tyto přejděte do jim **najít Symbol** okno nástroje. **Přejděte do definice** je obvykle užitečnější dvou. **Přejděte na deklaraci** bude deklarace najít než definice deklarace, jako je například třída friend – deklarace třídy nebo předávat odkazy.  
  
##  <a name="mfc_changes"></a> Krok 9. Změny MFC  
 Další chyba také má vztah k typu změněné deklarace a také výskytu v makru.  
  
```Output  
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'  
```  
  
 Problém je, že druhý parametr CWnd::OnActivateApp změnám z HTASK DWORD. K této změně došlo v 2002 verzi sady Visual Studio, Visual Studio .NET.  
  
```cpp  
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);  
```  
  
 Budeme muset aktualizovat deklarace OnActivateApp v odvozených třídách odpovídajícím způsobem následujícím způsobem:  
  
```cpp  
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);  
```  
  
 Snažíme se v tuto chvíli ke zkompilování projektu. Existuje několik upozornění fungovat prostřednictvím, ale a jsou volitelné části upgradu, jako je například převod z MBCS do kódu Unicode nebo zvýšení zabezpečení pomocí funkce zabezpečení CRT.  
  
##  <a name="compiler_warnings"></a> Krok 10. Adresování upozornění kompilátoru  
 Chcete-li získat úplný seznam upozornění, měli byste udělat **znovu vytvořit všechny** na řešení spíše než obyčejnou sestavení, stačí, abyste měli jistotu, že vše, co dříve zkompilovat bude zopakovat, vzhledem k tomu, že pouze získat upozornění sestavy z aktuální kompilace. Další otázka se jestli souhlasíte aktuální úroveň pro upozornění nebo používat vyšší úroveň pro upozornění.  Pokud přenášíte velké množství kódu, zejména původní kód, může být vhodné pomocí vyšší úroveň pro upozornění.  Můžete také chtít začít s výchozí úroveň pro upozornění a poté zvýšit úroveň pro upozornění k získání všech upozornění. Pokud používáte /Wall, dostanete upozornění. v systému soubory hlaviček, mnoho lidí používá /W4 získat většinu upozornění na svůj kód bez získávání upozornění pro systémové hlavičky. Pokud chcete upozornění objeví jako chyby, přidejte wdn možnost. Tato nastavení jsou v části C/C++ dialogové okno Vlastnosti projektu.  
  
 Jednu z metod ve třídě CSpyApp vyvolá upozornění o funkci, která již není podporována.  
  
```cpp  
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}  
```  
  
 Upozornění je následující.  
  
```Output  
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog  
```  
  
 Zpráva WM_CTLCOLORDLG již zpracovaných v nástroji Spy ++ kódu, tak byla vyžadována pouze změna odstranit všechny odkazy na SetDialogBkColor, které už nepotřebují.  
  
 Další upozornění se přehledné opravit komentářů na název proměnné. Dostali jsme následující upozornění:  
  
```Output  
warning C4456: declaration of 'lpszBuffer' hides previous local declaration  
```  
  
 Kód, který vytváří to zahrnuje makra.  
  
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
  
 Použití makra jako tento kód se obvykle byl kód těžší udržovat. V takovém případě makra obsahují deklarace proměnných. Makro parametr je definován následujícím způsobem:  
  
```cpp  
#define PARM(var, type, src)type var = (type)src  
```  
  
 Proto získá deklarovat proměnnou lpszBuffer dvakrát ve stejné funkci. Není tento straightfoward Chcete-li tento problém opravit, jako by šlo, pokud kód nebyly použití maker (jednoduše odebrat druhý deklaraci typu). Protože se jedná, máme velice nepříjemná volba museli rozhodnout, zda chcete přepsat kód makro jako obyčejnou kód (úloha zdlouhavé a které by mohly mít náchylný) nebo zakázat upozornění.  
  
 V takovém případě jsme opt zakázat upozornění. Můžete to přidáním pragma následujícím způsobem:  
  
```cpp  
#pragma warning(disable : 4456)  
```  
  
 Při zakazování upozornění, můžete chtít omezit zakázání ovlivňuje přesně takový kód, že vytváří upozornění, aby se zabránilo potlačení upozornění, když ho může poskytují užitečné informace. Nemůžeme přidat kód pro obnovení upozornění právě po řádku, která ho vytvořila, nebo ještě lepší, protože toto upozornění se zobrazí v makru, použijte `__pragma` – klíčové slovo, které funguje v makrech (`#pragma` nefunguje v makrech).  
  
```cpp  
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \  
type var = (type)src \  
__pragma(warning(default : 4456))  
  
```  
  
 Další upozornění vyžaduje některé revize kódu. GetVersion – rozhraní API Win32 (a GetVersionEx) je zastaralý.  
  
```Output  
warning C4996: 'GetVersion': was declared deprecated  
```  
  
 Následující kód ukazuje, jak získat verzi.  
  
```cpp  
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.  
DWORD dwWindowsVersion = GetVersion();  
  
```  
  
 Následují velké kód, který ověří dwWindowsVersion hodnotu k určení, zda jsme spuštěné v systému Windows 95 a kterou verzi systému Windows NT. Vzhledem k tomu, že se všechny zastaralé, jsme odebrat kód a řešit všechny odkazy na tyto proměnné.  
  
 Článek [změny verze operačního systému ve Windows 8.1 a Windows Server 2012 R2](https://msdn.microsoft.com/library/windows/desktop/dn302074.aspx) vysvětluje situaci.  
  
 Metod ve třídě CSpyApp dotaz na verzi operačního systému: IsWindows9x, IsWindows4x a IsWindows5x. Je to dobrý výchozí bod předpokládají, že verze systému Windows, který plánujeme zajistit podporu (Windows 7 a novější) jsou všechny zavřete na systému Windows NT 5 jako daleko technologie používá tento starší aplikace problémem. Použití těchto metod se řešení s omezeními starší operační systémy. Proto jsme změnili tyto metody vrátí hodnotu TRUE pro IsWindows5x a FALSE pro jiné.  
  
```cpp  
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }  
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }  
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }  
  
```  
  
 Která zůstane jen na několika místech, kde byly přímo používány interní proměnné. Vzhledem k tomu, že jsme odebrali tyto proměnné, se nám získat několik chyb, které mají explicitně řešit.  
  
```Output  
error C2065: 'm_bIsWindows9x': undeclared identifier  
```  
  
```cpp  
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)  
{  
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);  
}  
  
```  
  
 Jsme může nahradit toto volání metody nebo jednoduše pass hodnotu TRUE a odeberte starý zvláštní případ pro systém Windows 9 x.  
  
```cpp  
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)  
{  
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);  
}  
  
```  
  
 Poslední upozornění na výchozí úrovni (3) obsahuje dělat s bitfield.  
  
```Output  
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0  
```  
  
 Kód, který spustí toto je následující.  
  
```cpp  
m_bStdMouse = TRUE;  
```  
  
 Prohlášení o m_bStdMouse naznačuje, že je bitfield.  
  
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
  
 Tento kód byla zapsána před typu bool předdefinované byl podporován v jazyce Visual C++. V takový kód BOOL byla typedef pro int. Typ int je typ se znaménkem a bitová reprezentace podepsaný int, je použít první bit jako přihlašovací bit, tak bitfield typu int možné interpretovat jako představující 0 nebo -1, co byla pravděpodobně není určena.  
  
 Nebude vědět prohlížením kód důvodu jedná se o bitová pole. Byla cílem udržet co nejmenší velikost objektu, nebo je k dispozici kdekoli kde binární rozložení objektu slouží? Jsme změnili tyto členům BOOL obyčejnou vzhledem k tomu, že vidíte nebyl z nějakého důvodu pro použití bitfield. Pomocí bitová pole udržet co nejmenší velikost objektu není zaručena. To závisí na tom, jak kompilátor rozložen typ.  
  
 Může vás zajímat, pokud pomocí standardní typu bool v rámci mohou být užitečné. Řadu původní kód vzory, jako je typu BOOL byly vymyšlený k řešení problémů, které byly později Vyřešeno v standard C++, tak, aby změna z BOOL na předdefinovaný typ bool jenom jeden příklad takové změny, zvažte provádění po získání kódu původně spuštěna v nové verzi.  
  
 Jakmile jsme jste vyřešit všechny výstrahy, které se zobrazují na výchozí úrovni (úroveň 3) jsme změnili na úroveň 4 k zachycení několik dalších upozornění. První, zobrazí se následujícím způsobem:  
  
```Output  
warning C4100: 'nTab': unreferenced formal parameter  
```  
  
 Kód, který vytváří toto upozornění se následujícím způsobem.  
  
```cpp  
virtual void OnSelectTab(int nTab) {};  
```  
  
 Vypadá to dostatečně neškodné, ale vzhledem k tomu, že jsme chtěli čisté kompilace sadou /W4 a wdn, můžeme jednoduše označeno jako komentář název proměnné, zároveň je nechává v zájmu přehlednosti.  
  
```cpp  
virtual void OnSelectTab(int /*nTab*/) {};  
```  
  
 Další upozornění, které jsme obdrželi byly užitečné pro obecné kód čištění. Existuje několik implicitní převody z `int` nebo `unsigned int` k `WORD` (což je typedef pro `unsigned short`). Ty zahrnují možné ztrátě dat. Jsme přidali přetypování na `WORD` v těchto případech.  
  
 Další úroveň 4 upozornění, které jsme tu pro tento kód byl:  
  
```Output  
warning C4211: nonstandard extension used: redefined extern to static  
```  
  
 Tento problém nastane, když proměnná byla deklarována nejprve `extern`, později deklarovaný `static`. Význam tyto dvě specifikátory třídy úložiště se vzájemně vylučují, ale je to povoleno jako rozšíření Microsoft. Pokud jste chtěli kód přenosný na jiné kompilátory nebo jste chtěli kompilovat s /Za (režim kompatibility ANSI), změníte deklarace do mají odpovídající specifikátory třídy úložiště.  
  
##  <a name="porting_to_unicode"></a> Krok 11. Portování ze MBCS do kódu Unicode

 Všimněte si, že na světě Windows když říkáme kódování Unicode, jsme obvykle znamená UTF-16. Jiné operační systémy, jako je například Linux pomocí znakové sady UTF-8, ale Windows obecně neexistuje. MBCS verze knihovny MFC byla zrušena v sadě Visual Studio 2013 a 2015, ale už se nepoužívá v Visual Studio 2017. Pokud používáte Visual Studio 2013 nebo 2015, před provedením kroku k ve skutečnosti portu kód MBCS do kódu Unicode UTF-16, chceme může dočasně omezit upozornění, že je zastaralá MBCS, aby bylo možné provádět další činnosti nebo portování dokud vhodnou dobu odložit. Aktuální kód používá MBCS a chcete-li pokračovat, je potřeba nainstalovat verzi ANSI/MBCS MFC. Místo velké knihovny MFC není součástí výchozí sady Visual Studio **vývoj aplikací s jazykem C++** instalace, takže musíte ji vybrat z volitelných komponent v instalačním programu. V tématu [MFC MBCS DLL – doplněk](../mfc/mfc-mbcs-dll-add-on.md). Jakmile si stáhnout tuto a restartujte Visual Studio, můžete zkompilovat a propojit s verzí MFC MBCS, ale se jich zbavit upozornění o rozhraní MBCS Pokud používáte Visual Studio 2013 nebo 2015, měli byste také přidat **NO_WARN_MBCS_MFC_DEPRECATION**do seznamu předdefinovaná makra v části preprocesoru vlastnosti projektu, nebo na začátku souboru stdafx.h záhlaví nebo jiné běžné hlavičky souborů.  
  
 Nyní je k dispozici chybami linkeru.  
  
```Output  
fatal error LNK1181: cannot open input file 'mfc42d.lib'  
```  
  
 LNK1181 dochází, protože na verzi zastaralé statické knihovny mfc je zahrnuta v linkeru vstup. Není to povinné už, protože jsme můžete propojit MFC dynamicky, takže potřebujeme odeberte všechny statické knihovny MFC z vlastnosti vstupu v části Linker vlastností projektu. Tento projekt je také pomocí možnosti /NODEFAULTLIB a místo toho jsou uvedeny všechny závislosti knihovny.  
  
```  
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)  
```  
  
 Nyní dejte nám ve skutečnosti aktualizujte kód staré vícebajtové znakovou sadu (MBCS) na kódování Unicode. Vzhledem k tomu, že toto je aplikace systému Windows, důvěrně svázané s platformou Windows desktop jsme se portu na kódování Unicode UTF-16, které používá systém Windows. Při psaní kódu pro různé platformy nebo portování aplikace systému Windows na jiné platformě, můžete zvážit portování do znakové sady UTF-8, které se často používá v jiných operačních systémech.  
  
 Portování do kódu Unicode UTF-16, jsme musíte rozhodnout, zda stále chceme možnost zkompilovat do MBCS nebo ne.  Pokud Chceme mít možnost pro podporu MBCS, bychom měli použít Tchar – makro jako typ znak, který přeloží na buď `char` nebo `wchar_t`, v závislosti na tom, jestli je definována _MBCS nebo _UNICODE během kompilace. Přepnutí na Tchar – a Tchar – verzích různých rozhraních API místo `wchar_t` a jeho přidružené rozhraní API znamená, že můžete vrátit zpět na verzi MBCS kódu jednoduše tak, že definujete _MBCS makro místo _UNICODE. Kromě Tchar – existuje různých verzí Tchar – například často používaný – definice TypeDef, makra a funkce. Například LPCTSTR místo LPCSTR a tak dále. V dialogovém okně Vlastnosti projektu v části **vlastnosti konfigurace**v **Obecné** změňte **znaková sada** vlastnost z **použití MBCS Znaková sada** k **použít sadu znak Unicode**. Toto nastavení ovlivňuje, které makro je předdefinovaná během kompilace. Je makro kódování UNICODE a _UNICODE – makro. Vlastnosti projektu ovlivňuje i konzistentně. Záhlaví systému Windows pomocí kódování UNICODE, kde hlavičky Visual C++, jako je například MFC použít _UNICODE, ale pokud je definován, dalších vždy definována.  
  
 Dobrou [průvodce](http://msdn.microsoft.com/library/cc194801.aspx) portování z MBCS do kódu Unicode UTF-16 pomocí Tchar – existuje. Vybereme možnost této trasy. Nejprve se nám změnit **znaková sada** vlastnost **použití Unicode znaková sada** a projekt znovu sestavte.  
  
 Některé místech kód již používali `TCHAR`, zdá v očekávání nakonec Podpora kódování Unicode. Některé nebyly. Jsme hledali instancí `CHAR`, což je definice typu char a nahrazené většina z nich s Tchar –. Také jsme hledán `sizeof (CHAR)`. Vždy, když jsme změnili z `CHAR` k `TCHAR`, jsme obvykle měl změnit na `sizeof(TCHAR)` vzhledem k tomu, že to se často používá k určení počtu znaků v řetězci. Pomocí nesprávného typu zde nevytváří chybu kompilátoru, takže je vhodné platícího kousek pozornost tento případ.  
  
 Tohoto typu chyby je velmi běžné právě po přepnutí na kódování Unicode.  
  
```Output  
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'  
```  
  
 Tady je příklad kódu, který vytváří toto:  
  
```cpp  
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);  
```  
  
 Jsme uveďte _T kolem řetězec literálu odebrat chyba.  
  
```cpp  
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);  
```  
  
 _T – makro má za následek provedení literálu kompilace řetězec jako `char` řetězec nebo `wchar_t` řetězec, v závislosti na nastavení MBCS nebo UNICODE. Pokud chcete nahradit všechny řetězce _T v sadě Visual Studio, poprvé otevřete **rychle nahradit** (klávesnice: Ctrl + F) pole nebo **nahradit v souborech** (klávesnice: Ctrl + Shift + H), zvolte **použití regulárních Výrazy** zaškrtávací políčko. Zadejte `((\".*?\")|('.+?'))` jako hledaný text a `_T($1)` jako Nahrazovací text. Pokud již máte _T – makro kolem některé řetězce, tento postup se ji znovu přidejte a setkat i případy, kdy nechcete _T, například při použití `#include`, takže je vhodné použít **nahradit další** místo  **Nahraďte všechny**.  
  
 Tato konkrétní funkce [wsprintf](https://msdn.microsoft.com/library/windows/desktop/ms647550.aspx), je ve skutečnosti definován v záhlaví systému Windows a v dokumentaci pro doporučí, že ho nelze použít, z důvodu přetečení možné vyrovnávací paměti. Pro je uvedena velikost `szTmp` vyrovnávací paměti, takže neexistuje žádný způsob pro funkce, které chcete zkontrolovat, že vyrovnávací paměti může obsahovat všechna data, která má být zapsán do ní. Najdete v další části o přenos do zabezpečení CRT, ve kterém jsme jiné podobné problémy opravit. Jsme skončila jeho nahrazením [_stprintf_s –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md).  
  
 Další běžnou chybou, které se zobrazí v převodu na kódování Unicode je to.  
  
```Output  
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'  
```  
  
 Kód, který ho generuje vypadá takto:  
  
```cpp  
pParentNode->m_szText = new char[strTitle.GetLength() + 1];  
_tcscpy(pParentNode->m_szText, strTitle);  
  
```  
  
 I když _tcscpy – funkce byl použit, což je Tchar – strcpy – funkce pro kopírování řetězec, byl vyrovnávací paměti, která byla přidělena `char` vyrovnávací paměti. Snadno se změní na Tchar –.  
  
```cpp  
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];  
_tcscpy(pParentNode->m_szText, strTitle);  
  
```  
  
 Podobně jsme změnili `LPSTR` (dlouho ukazatel na řetězec) a `LPCSTR` (dlouho ukazatel na konstantní řetězec) k `LPTSTR` (dlouho ukazatel Tchar – řetězec) a `LPCTSTR` (dlouho ukazatel na konstantní řetězec Tchar –), při oprávněných z Chyba kompilátoru. Jsme zvolili Nedělejte nahrazení pomocí globální Hledat a nahradit, protože každé situaci měl prověřit, jednotlivě. V některých případech `char` chtěli verze, například při zpracování určitých Windows zpráv, které používat struktury systému Windows, které mají příponu A. V rozhraní Windows API příponu A znamená ASCII nebo ANSI (a platí také pro MBCS) a příponou W znamená široké znaky, nebo Unicode UTF-16. Tato vzoru pro pojmenovávání se používá v hlavičkách Windows, ale jsme také a potom ji v kódu nástroje Spy ++ když jsme měli přidat Unicode verze funkce, která již byla definována ve pouze MBCS verzi.  
  
 V některých případech nám museli nahradit typ má být použit na verzi, která přeloží správně (WNDCLASS místo WNDCLASSA např.).  
  
 V řadě případů jsme museli používat obecná verzi (makro) Win32 API jako GetClassName (namísto GetClassNameA). V příkazu switch obslužné rutiny zpráv, některé zprávy jsou konkrétní MBCS nebo Unicode, v těchto případech, jsme musel měnit kód explicitně volání MBCS verze, protože jsme nahradit funkce obecně s názvem se a W specifické funkce a přidat makro pro Obecný název, který se přeloží na správné A nebo W název založený na tom, zda je definována kódování UNICODE.  V mnoha části kódu když jsme přešli na definovat _UNICODE, W verze je nyní vybrali i v případě verze A je co je chtěli.  
  
 Nejsou k dispozici na několika místech, kde museli věnovat zvláštní akce. Jakékoli použití WideCharToMultiByte nebo MultiByteToWideChar může vyžadovat bližší pohled. Zde je příkladem, kde se používá WideCharToMultiByte.  
  
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
  
 Chcete-li to vyřešit, jsme měli zjistit, že důvod, proč k tomu bylo potřeba bylo kopírování široká znaková řetězec reprezentující název písmo do vnitřní vyrovnávací paměť CString, strFace. To vyžaduje mírně odlišný kód pro vícebajtové CString řetězce jako široká znaková CString řetězce, takže jsme přidali #ifdef v tomto případě.  
  
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
  
 Samozřejmě místo wcscpy – jsme skutečně by měl použít wcscpy_s –, bezpečnější verze. Tuto situaci řeší v další části.  
  
 Pro kontrolu našich pracovních jsme použití vícebajtových znaková sada obnovit znaková sada a ujistěte se, že kód stále shromažďování, použití MBCS, jakož i kódování Unicode. Needless znamená průchodu úplné testu musí provést u rekompilované aplikace po tyto změny.  
  
 V našem pracují se toto řešení nástroje Spy ++ trvalo o dvou dnů pro vývojář průměrná C++ převést kód na kódování Unicode. Retesting čas neobsahuje.  
  
##  <a name="porting_to_secure_crt"></a> Krok 12. Portování používat zabezpečení CRT  
 Portování kódu pro použití zabezpečeného verze funkcí CRT (verze s příponou _Malá) je další. V takovém případě je funkce nahraďte _M verze a potom obvykle přidat parametry velikost vyrovnávací paměti vyžaduje další obecné strategie. V mnoha případech jde přehledné vzhledem k tomu, že velikost je známý. V ostatních případech, kde velikost není ihned k dispozici, je potřeba přidat další parametry funkce, která používá funkci CRT nebo možná zkontrolujte využití cílové vyrovnávací paměti a najdete v části co odpovídající velikost jsou omezení.  
  
 Visual C++ poskytuje podvodné, aby bylo snazší získat zabezpečený kód bez přidání tolik parametrů velikost a který je pomocí šablony přetížení. Vzhledem k tomu, že tato přetížení jsou šablony, že jsou dostupná pouze při kompilování jako C++, není jako C. Spyxxhk je projekt C, takže nebudou fungovat efektu pro tento.  Však není Spyxx a používáme podvodné. Základem je na místě, kde se bude zkompilován v každém souboru projektu, například v stdafx.h přidá řádek takto:  
  
```cpp  
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1  
```  
  
 Když definujete, vždy, když vyrovnávací paměť je pole, namísto nezpracovaná ukazatele, je její velikosti odvodit z typ pole a který slouží jako parametr velikosti, aniž by bylo nutné ho zadat. Který pomáhá omezit složitosti přepisování kód. Je třeba nahradit název funkce _M verzí, ale který často se dá dělat formou vyhledávání a operace nahrazování.  
  
 Návratové hodnoty některé funkce změnit. Například _itoa_s – (a _itow_s – a _itot_s – makro) vrátí kód chyby (errno_t), nikoli řetězec. Proto v těchto případech je nutné přesunout volání _itoa_s – na samostatném řádku a nahraďte ji metodou identifikátor do vyrovnávací paměti.  
  
 Některé běžné případy: pro memcpy – při přechodu k memcpy_s – jsme přidali často velikost strukturu byly zkopírovány na. Podobně pro většinu řetězce a vyrovnávacích pamětí, velikost pole nebo vyrovnávací paměti je snadno určit deklaraci vyrovnávací paměti nebo hledání, kde byla původně přidělit vyrovnávací paměť. Pro některé situace je nutné určit, jak velký vyrovnávací paměti je ve skutečnosti k dispozici, a pokud tyto informace není k dispozici v rámci oboru funkce, který upravujete, by měl být přidán jako dodatečný parametr a volající kód by měl být upraven na Zadejte informace.  
  
 Pomocí těchto postupů převést kódu pro použití zabezpečeného funkcí CRT trvalo asi půl za den. Pokud si zvolíte možnost Ne přetížení šablony a k přidání parametrů velikost ručně, by pravděpodobně trvat dvakrát nebo třikrát delší dobu.  
  
##  <a name="deprecated_forscope"></a> Krok 13. /Zc:forScope-je zastaralý.  
 Od verze Visual C++ verze 6.0 kompilátor vyhovuje aktuální standard, což omezí obor proměnných deklarovaných ve smyčce do oboru smyčky. Možnost kompilátoru [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) (**vynutit dodržování pro obor cyklu for** ve vlastnostech projektu) určuje, zda bude ohlášena za chybu. Jsme by měl aktualizovat kódu jako vyhovující a přidejte deklarace právě mimo smyčku. Aby se zabránilo provedení změn kódu, můžete změnit toto nastavení v části jazyk C++ vlastností projektu a **žádné (/Zc:forScope-)**. Nicméně, mějte na paměti, **/Zc:forScope-** může být odebrán v budoucí verzi Visual C++, takže nakonec váš kód bude nutné změnit tak, aby odpovídala na standardní.  
  
 Tyto problémy jsou je poměrně snadné ho opravit, ale v závislosti na kódu, může to ovlivnit velké množství kódu. Zde je typické problém.  
  
```cpp  
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const  
{  
  for (int n = 0; mszStrings[0] != 0; n++)  
  mszStrings = _tcschr(mszStrings, 0) + 1;  
  return(n);  
}  
  
```  
  
 Výše uvedený kód vytvoří následující chyba:  
  
```Output  
'n': undeclared identifier  
```  
  
 K tomu dochází, protože kompilátor se nepoužívá možnost kompilátoru, která povolené kód, který není v souladu se standardní C++. Ve verzi standard se deklarace proměnné uvnitř smyčky omezuje jeho oboru smyčky pouze, takže běžnou praxí pomocí smyčky čítač mimo smyčky vyžaduje, aby deklaraci čítač také přesunout mimo smyčky, jako v následujícím kódu revidované :  
  
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
 Portování nástroje Spy ++ z původní kódu Visual C++ verze 6.0 nejnovější kompilátoru trvalo asi 20 hodin kódování o týden v průběhu času. Nemůžeme upgradovat přímo přes osm verze produktu Visual Studio 6.0 na Visual Studio 2015. To se teď doporučený postup pro všechny upgrady v projektech malé i velké.  
  
## <a name="see-also"></a>Viz také  
 [Portování a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Předchozí Případová studie: COM Spy](../porting/porting-guide-com-spy.md)