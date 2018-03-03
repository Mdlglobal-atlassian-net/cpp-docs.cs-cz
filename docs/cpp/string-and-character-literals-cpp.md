---
title: "Řetězcové a znakové literály (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- R
dev_langs:
- C++
helpviewer_keywords:
- L constant
- escape sequences
- Null strings, null-terminated strings
- literal strings, C++
- Null strings
- string literals, syntax
- string literals
- literal strings
- strings [C++], string literals
- NULL, character constant
- wide characters, strings
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37e5b86dfdef9c49e0e59c28d36ba4622238eced
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="string-and-character-literals--c"></a>Řetězcové a znakové literály (C++)
C++ podporuje různé typy řetězce a znak a poskytuje způsoby, jak express literálových hodnot každé z těchto typů. Ve zdrojovém kódu express obsah vaší znak a řetězec literály pomocí znakovou sadu. Univerzální názvy znaků a řídicí znaky umožňují express libovolného řetězce základní zdrojové znakové sadě. Nezpracovaná řetězcový literál umožňuje vyhnout řídicí znaky a slouží k express všechny typy textových literálů. Můžete také vytvořit std::string literály bez nutnosti provádět navíc konstrukce nebo převod kroky.  
  
```cpp  
#include <string>  
using namespace std::string_literals; // enables s-suffix for std::string literals  
  
int main()  
{  
    // Character literals  
    auto c0 =   'A'; // char  
    auto c1 = u8'A'; // char  
    auto c2 =  L'A'; // wchar_t  
    auto c3 =  u'A'; // char16_t  
    auto c4 =  U'A'; // char32_t  
  
    // String literals  
    auto s0 =   "hello"; // const char*  
    auto s1 = u8"hello"; // const char*, encoded as UTF-8  
    auto s2 =  L"hello"; // const wchar_t*  
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16  
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32  
  
    // Raw string literals containing unescaped \ and "  
    auto R0 =   R"("Hello \ world")"; // const char*  
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8  
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*  
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16  
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32  
  
    // Combining string literals with standard s-suffix  
    auto S0 =   "hello"s; // std::string  
    auto S1 = u8"hello"s; // std::string  
    auto S2 =  L"hello"s; // std::wstring  
    auto S3 =  u"hello"s; // std::u16string  
    auto S4 =  U"hello"s; // std::u32string  
  
    // Combining raw string literals with standard s-suffix  
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*  
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8  
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*  
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16  
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32  
}  
```  
  
 Textové literály může mít žádná předpona nebo `u8`, `L`, `u`, a `U` předpony k označení zúžit znak (jednobajtové nebo vícebajtové), ve formátu UTF-8, široké znak (UCS-2 nebo UTF-16), UTF-16 a kódování UTF-32 v uvedeném pořadí. Nezpracovaná řetězcový literál může mít `R`, `u8R`, `LR`, `uR` a `UR` předpon pro ekvivalenty nezpracovaná verze těchto kódování.  Pokud chcete vytvořit std::string dočasné nebo statické hodnoty, můžete použít textové literály nebo nezpracovaná textové literály s `s` příponu. Další informace najdete v části literály řetězce níže. Další informace o znak základní zdroje nastavit univerzální názvy znaků a pomocí znaky z rozšířené kódové stránky ve zdrojovém kódu, najdete v tématu [znakových sad](../cpp/character-sets2.md).  
  
## <a name="character-literals"></a>Znakové literály  
 A *znakový literál* se skládá z konstantní znak. Je zobrazena ve znaku v jednoduchých uvozovkách. Existují pět druhy znakové literály:  
  
-   Obyčejnou znakové literály typu `char`, například`'a'`  
  
-   Znakové sady UTF-8 znakové literály typu `char`, například`u8'a'`  
  
-   Celou znakové literály typu `wchar_t`, například`L'a'`  
  
-   Znakové sady UTF-16 znakové literály typu `char16_t`, například`u'a'`  
  
-   Znakové sady UTF-32 znakové literály typu `char32_t`, například`U'a'`  
  
 Znak použitý pro literálu znak může být libovolný znak, s výjimkou vyhrazené znaky zpětné lomítko ('\\'), jednoduché uvozovky ('), nebo nový řádek. Vyhrazené znaky lze zadat pomocí řídicí sekvence. Znaků můžete zadat pomocí univerzální názvy znaků, tak dlouho, dokud typ je dostatečně velký pro uložení znak.  
  
### <a name="encoding"></a>Kódování  
 Znakové literály zakódovaným odlišně na základě jejich předpony.  
  
-   Literál bez předpony znak je literál obyčejnou znak. Hodnota znakem obyčejnou literálu jeden znak, který obsahuje řídicí sekvenci nebo název universal znak, který může být reprezentován v znaková sada spuštění má hodnotu rovnou hodnotě číselné kódování v znaková sada spuštění. Obyčejnou znakem literálu obsahující více než jeden znak, – řídicí sekvence nebo název universal znak je *multicharacter literálu*. Multicharacter literál nebo obyčejnou znakový literál, který nelze v znaková sada spuštění je podmíněně nepodporují, má typ int, a jeho hodnota může být definované implementací.  
  
-   Znakový literál, který začíná předponu L je široká charakterová literál. Hodnota široká charakterová literál obsahující jeden znak, – řídicí sekvence nebo universal znak name má hodnotu rovna hodnotě číselné kódování celou-znakem spouštění nastavit, pokud znakový literál nemá zastoupení celou znaková sada spuštění, v takovém případě hodnota je definované implementací. Široká charakterová literál obsahující více znaků, řídicí sekvence nebo univerzální názvy znaků hodnotu definované implementací.  
  
-   Znakový literál, který začíná předponu u8 je literál UTF-8 znaků. Hodnota literálu UTF-8 znak obsahující jeden znak, řídicí sekvenci nebo universal znak name má hodnotu rovnou hodnotě bodu kódu jeho ISO 10646, pokud může být reprezentovaný jedné jednotky kódu UTF-8 (odpovídající C0 ovládací prvky a základní Latinské Unicode blok). Pokud hodnota nemůže být reprezentovaná jedné jednotky kódu UTF-8, program má chybný formát. Znakové sady UTF-8 znak literálu obsahující více než jeden znak, – řídicí sekvence nebo název universal znak je nesprávně vytvořen.  
  
-   Znakový literál, který začíná předponu u je literál UTF-16 znaků. Hodnota literálu UTF-16 znak obsahující jeden znak, řídicí sekvenci nebo universal znak name má hodnotu rovnou hodnotě bodu kódu jeho ISO 10646, pokud může být reprezentovaný jedné jednotky kódu UTF-16 (odpovídající základní vícejazyčnou roviny ). Pokud hodnota nemůže být reprezentovaná jedné jednotky kódu UTF-16, program má chybný formát. Znakové sady UTF-16 znak literálu obsahující více než jeden znak, – řídicí sekvence nebo název universal znak je nesprávně vytvořen.  
  
-   Znakový literál, který začíná předponu U je literál znakové sady UTF-32 znaků. Hodnota literálu znakové sady UTF-32 znak obsahující jeden znak, řídicí sekvenci nebo universal znak name má hodnotu rovna hodnotě bodu kódu jeho ISO 10646. Znakové sady UTF-8 znak literálu obsahující více než jeden znak, – řídicí sekvence nebo název universal znak je nesprávně vytvořen.  
  
###  <a name="bkmk_Escape"></a>Řídicí sekvence  
 Existují tři druhy řídicí sekvence: jednoduchý, osmičkových a šestnáctkových. Řídicí sekvence může být jedno z následujících:  
  
|Hodnota|Řídicí sekvence|Hodnota|Řídicí sekvence|  
|-----------|---------------------|-----------|---------------------|  
|newline|\n|zpětné lomítko|\\\|  
|Vodorovné karty|\t|otazník|? nebo \\?|  
|vertikální tabulátor|\v|jednoduché uvozovky|\\'|  
|BACKSPACE|\b|dvojité uvozovky|\\"|  
|návrat na začátek řádku|\r|znak hodnoty null|\0|  
|řídicí znak|\f|osmičkové|\ooo|  
|Výstraha (zvonku)|\a|hexadecimální|\xhhh|  
  
 Následující kód ukazuje několik příkladů uvozený znaků pomocí obyčejnou znakové literály. Stejná syntaxe řídicí sekvence je platný pro další znak literálu typy.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    char newline = '\n';  
    char tab = '\t';  
    char backspace = '\b';  
    char backslash = '\\';  
    char nullChar = '\0';  
  
    cout << "Newline character: " << newline << "ending" << endl; // Newline character:  
                                                                  //  ending  
    cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending  
    cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending  
    cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending  
    cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending  
}  
```  
  
 **Konkrétní Microsoft**  
  
 Pokud chcete vytvořit hodnotu z znakem obyčejnou literálu (těch bez předpony), převede kompilátor znak nebo posloupnost znaků mezi jednoduchých uvozovek a být do 8bitové hodnoty v 32bitové celé číslo. Více znaků v literálové vyplní odpovídající bajtů potřeby z horní nejnižší. Chcete-li vytvořit `char` hodnota, kompilátor má nejnižší bajtů. Chcete-li vytvořit `wchar_t` nebo `char16_t` hodnota, kompilátor má nejnižší word. Kompilátor varovat, pokud jsou výše přiřazené bajtů nebo slovo všechny služby bits se zkrátí výsledek.  
  
```cpp  
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'  
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'  
```  
  
 Osmičková řídicí sekvence je zpětné lomítko následované posloupnost až 3 osmičková číslice. Chování osmičková řídicí sekvence, které pravděpodobně obsahuje více než tří číslic je považován za 3 číslice osmičková pořadí, za nímž následuje následných číslic jako znaků; To může poskytnout překvapivé výsledky. Příklad:  
  
```cpp  
char c1 = '\100';   // '@'  
char c2 = '\1000';  // C4305, C4309, truncates to '0'   
```  
  
 Řídicí sekvence, které se zobrazují tak, aby obsahovala-osmičkové znaky, jsou vyhodnoceny jako v osmičková sekvenci až do posledního osmičková znaku, za nímž následuje ostatní znaky. Příklad:  
  
```cpp  
char c3 = '\009';   // '9'  
char c4 = '\089';   // C4305, C4309, truncates to '9'  
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'  
```  
  
 Šestnáctková řídicí sekvence je zpětné lomítko následuje znak `x`, za nímž následují sekvenci hexadecimálních číslic. Řídicí sekvence, který obsahuje žádné šestnáctkové číslice způsobí, že chyba kompilátoru C2153: "šestnáctkové literály musí mít alespoň jeden číslice v hexadecimálním formátu". Úvodní nuly se ignorují. Řídicí sekvence, který zřejmě není šestnáctkový a šestnáctkových znaků je vyhodnoceno jako šestnáctková řídicí sekvence až poslední znak hexadecimální následované znaky není šestnáctkový.   V obyčejnou předponu u8 znak nebo literálu je nejvyšší šestnáctkové hodnoty 0xFF. V předpony L předponu u široké znak nebo literálu je nejvyšší šestnáctkové hodnoty 0xFFFF. V předponu U široký znak literálu je nejvyšší šestnáctkové hodnoty 0xFFFFFFFF.  
  
```cpp  
char c6 = '\x0050'; // 'P'  
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'  
```  
  
 Pokud široký znak literálu předponu `L` obsahuje více než jeden znak, tato hodnota je převzata z první znak. Následující znaky jsou ignorovány, na rozdíl od chování ekvivalentní obyčejnou znaku literálu.  
  
```cpp  
wchar_t w1 = L'\100';   // L'@'  
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored   
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored  
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored  
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored  
wchar_t w6 = L'\x0050'; // L'P'  
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored  
```  
  
 **Konkrétní Microsoft END**  
  
 Znak zpětného lomítka (\\) je znak pokračování řádku, pokud je umístěn na konci řádku. Pokud chcete znak zpětného lomítka se objeví jako znak literálu, je nutné zadat dvě zpětná řádek (`\\`). Další informace o znak pro pokračování řádku najdete v tématu [fáze překladu](../preprocessor/phases-of-translation.md).  
  
###  <a name="bkmk_UCN"></a>Univerzální názvy znaků  
 V znakové literály a nativní (bez – hrubá, nezpracovaná) textové literály může představovat libovolný znak název universal znak.  Univerzální názvy znaků jsou tvořeny předpony, které následují \U bodem kódu Unicode v řádu osm, nebo předponu \u následuje bod kódování Unicode čtyři číslice. Všechny osm nebo čtyři číslice, v uvedeném pořadí, musí být přítomen, aby název ve správném formátu universal znak.  
  
```cpp  
char u1 = 'A';          // 'A'  
char u2 = '\101';       // octal, 'A'   
char u3 = '\x41';       // hexadecimal, 'A'  
char u4 = '\u0041';     // \u UCN 'A'  
char u5 = '\U00000041'; // \U UCN 'A'  
```  
  
 **Náhradní dvojice**  
  
 Univerzální názvy znaků nelze dekódovat z hodnoty v rozsahu bodu kódu náhradní D800 DFFF. Pro dvojice náhradní znakové sady Unicode, zadejte název universal znak pomocí `\UNNNNNNNN`, kde je NNNNNNNN bodem kódem znaku. Kompilátor generuje náhradní pár v případě potřeby.  
  
 V C ++ 03 jazyk pouze povolené podmnožinu znaků, který má být reprezentovaná jejich univerzální názvy znaků a povolené některé názvy universal znaků, které ve skutečnosti nepředstavovala platnou znaky Unicode. To byla opravena v C ++ 11 standardní. V C ++ 11 můžete použít řetězec a znakové literály a identifikátory univerzální názvy znaků.  Další informace o univerzální názvy znaků, najdete v části [znakových sad](../cpp/character-sets2.md). Další informace o Unicode najdete v tématu [Unicode](http://msdn.microsoft.com/library/dd374081\(v=vs.85\).aspx). Další informace o náhradní dvojice najdete v tématu [náhradní dvojice a doplňkové znaky](http://msdn.microsoft.com/library/dd374069\(v=vs.85\).aspx).  
  
## <a name="string-literals"></a>Textové literály  
 Řetězcový literál představuje posloupnosti znaků, které společně tvoří řetězce ukončené hodnotou null. Znaky musí být uzavřena mezi znaky uvozovek. Existují následující typy textových literálů:  
  
### <a name="narrow-string-literals"></a>Úzké textové literály  
 Je omezený řetězcový literál bez předponu, dvojité uvozovky s oddělovači, ukončené hodnotou null pole typu `const char[n]`, kde n je délka pole v bajtech. Úzké řetězcový literál může obsahovat libovolný znak grafické kromě dvojité uvozovky (`"`), zpětné lomítko (`\`), nebo znak nového řádku. Názvy uvedené výše a univerzální znak řídicí sekvence, které nevešla bajt může obsahovat také úzké řetězcový literál.  
  
```cpp  
const char *narrow = "abcd";  
  
// represents the string: yes\no  
const char *escaped = "yes\\no";  
```  
  
#### <a name="utf-8-encoded-strings"></a>Řetězce kódovaného ve formátu UTF-8  
  
 Řetězec formátu UTF-8 je u8 předponu, dvojité uvozovky s oddělovači, ukončené hodnotou null pole typu `const char[n]`, kde n je délka kódovaného pole v bajtech. Řetězcový literál předponu u8 může obsahovat libovolný znak grafické kromě dvojité uvozovky (`"`), zpětné lomítko (`\`), nebo znak nového řádku. Řetězcový literál předponu u8 můžou taky obsahovat řídicí, které pořadí uvedené výše a libovolný název universal znak.  
  
```cpp  
const char* str1 = u8"Hello World";  
const char* str2 = u8"\U0001F607 is O:-)";  
```  
  
### <a name="wide-string-literals"></a>Široké textové literály  
 Široké řetězcový literál je ukončené hodnotou null řadu konstanta `wchar_t` , je předponu "`L`a obsahuje všechny grafické znaku kromě dvojité uvozovky ("), zpětné lomítko (\\), nebo znak nového řádku. Široké řetězcový literál může obsahovat řídicí, které pořadí uvedené výše a libovolný název universal znak.  
  
```cpp  
const wchar_t* wide = L"zyxw";  
const wchar_t* newline = L"hello\ngoodbye";  
```  
  
#### <a name="char16t-and-char32t-c11"></a>char16_t a char32_t (C ++ 11)  
  
 C ++ 11 představuje přenosný počítač `char16_t` (16bitové Unicode) a `char32_t` (32bitová verze Unicode) znak typy:  
  
```cpp  
auto s3 = u"hello"; // const char16_t*  
auto s4 = U"hello"; // const char32_t*  
```  
  
### <a name="raw-string-literals-c11"></a>Nezpracovaný řetězec literály (C ++ 11)  
 Nezpracovaná řetězcový literál je pole ukončené hodnotou null – znak typu – obsahující libovolný grafické znak, včetně dvojité uvozovky ("), zpětné lomítko (\\), nebo znak nového řádku. Nezpracovaný řetězec literály se často používají v regulárních výrazech, které používají třídy znaků a řetězce HTML a XML řetězce. Příklady, najdete v následujícím článku: [Bjarnem Stroustrupem – nejčastější dotazy na C ++ 11](http://go.microsoft.com/fwlink/p/?linkid=401172).  
  
```cpp  
// represents the string: An unescaped \ character  
const char* raw_narrow = R"(An unescaped \ character)";  
const wchar_t* raw_wide = LR"(An unescaped \ character)";  
const char*       raw_utf8  = u8R"(An unescaped \ character)";  
const char16_t* raw_utf16 = uR"(An unescaped \ character)";  
const char32_t* raw_utf32 = UR"(An unescaped \ character)";  
```  
  
 Oddělovač je uživatelem definované posloupnost až 16 znaků, která okamžitě předchází levé závorky nezpracovaná literálu řetězce a následuje jeho kulaté závorky.  Například v `R"abc(Hello"\()abc"` pořadí oddělovač je `abc` a řetězec obsah je `Hello"\(`. Oddělovač můžete použít k rozlišení nezpracovaná řetězce, které obsahují dvojité uvozovky i závorek. To způsobí, že chyba kompilátoru:  
  
```cpp  
// meant to represent the string: )"  
const char* bad_parens = R"()")";  // error C2059  
```  
  
 Ale oddělovač přeloží ji:  
  
```cpp  
const char* good_parens = R"xyz()")xyz";  
```  
  
 Můžete vytvořit nezpracovaná řetězcový literál je nový řádek (ne řídící znak) ve zdroji:  
  
```cpp  
// represents the string: hello  
//goodbye  
const wchar_t* newline = LR"(hello  
goodbye)";  
```  
  
### <a name="stdstring-literals-c14"></a>std::String literály (C ++ 14)  
 literály std::String jsou standardní knihovna implementace uživateli definované literály (viz níže), které jsou reprezentovány jako s "xyx" (s `s` přípony). Tento druh řetězcový literál vytvoří dočasný objekt typu std::string, std::wstring, std::u32string nebo std::u16string v závislosti na předponu, která je zadána. Pokud je použita žádná předpona, jako výše, std::string vytváří. L "xyz" s vytvoří std::wstring. u "xyz" s vytváří [std::u16string](../standard-library/string-typedefs.md#u16string)a U "xyz" s vytváří [std::u32string](../standard-library/string-typedefs.md#u32string).  
  
```cpp  
//#include <string>  
//using namespace std::string_literals;  
string str{ "hello"s };  
string str2{ u8"Hello World" };  
wstring str3{ L"hello"s };  
u16string str4{ u"hello"s };  
u32string str5{ U"hello"s };  
```  
  
 Přípona s jde použít taky u literály Nezpracovaný řetězec:  
  
```cpp  
u32string str6{ UR"(She said "hello.")"s };  
```  
  
 literály std::String jsou definovány v oboru názvů `std::literals::string_literals` v \<řetězec > soubor hlaviček. Protože `std::literals::string_literals`, a `std::literals` jsou deklarovány jako [obory názvů vložené](../cpp/namespaces-cpp.md), `std::literals::string_literals` je automaticky zpracován jako náležela přímo v oboru názvů `std`.  
  
### <a name="size-of-string-literals"></a>Velikost textové literály  
 Pro ANSI char\* řetězce a další jednobajtové kódování (není ve formátu UTF-8), velikost řetězcový literál (v bajtech) je počet znaků a 1 pro ukončující znak hodnoty null. Pro všechny ostatní typy řetězec nesouvisí velikost výhradně pro počet znaků. Znakové sady UTF-8 používá ke kódování některé až čtyři elementy char *code jednotky*a char16_t nebo wchar_t kódovaný jako UTF-16 může použít dva elementy (pro celkový počet bajtů čtyři) určený ke kódování jedné *jednotka kódu*.   Tento příklad ukazuje velikost široké řetězce literálu v bajtech:  
  
```cpp  
const wchar_t* str = L"Hello!";  
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);  
```  
  
 Všimněte si, že `strlen()` a `wcslen()` nezahrnují velikost ukončující prázdný znak, jehož velikost odpovídá velikost elementu na řetězcový typ.: jeden bajtů na řetězec char *, dva bajty na wchar_t\* nebo char16_t\* řetězce, a čtyři bajtů na char32_t\* řetězce.  
  
 Maximální délka řetězcový literál je 65535 bajtů. Toto omezení se vztahuje k úzké textové literály a široké textové literály.  
  
### <a name="modifying-string-literals"></a>Úprava textové literály  
 Protože textové literály (včetně není std:string literály) jsou konstanty, pokusu o změnu je – například str [2] = "A" – způsobí chybu kompilátoru.  
  
 **Konkrétní Microsoft**  
  
 V jazyce Visual C++ můžete řetězcový literál k chybě při inicializaci ukazatel na jiný const `char` nebo `wchar_t`. Toto je povolena v C99 kód, ale je zastaralé v C ++ 98 a odebrat C ++ 11. Pokus upravit řetězec způsobí, že porušení přístupu, jako v následujícím příkladu:  
  
```cpp  
wchar_t* str = L"hello";  
str[2] = L'a'; // run-time error: access violation  
```  
  
 Může způsobit kompilátoru pro generování k chybě při převodu řetězcový literál ukazatel znak non_const při nastavení [/Zc: strictstrings (zakázání převodů typů řetězcových literálů)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) – možnost kompilátoru. Doporučujeme ho pro standardům přenosné kódu. Je také vhodné používat `auto` – klíčové slovo deklarovat řetězec inicializovat literál ukazatele, protože se přeloží na správného typu (#const). Tento příklad kódu například zachytí pokus o zápis do řetězcový literál v době kompilace:  
  
```cpp  
auto str = L"hello";  
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.  
```  
  
 V některých případech může být identické textové literály fondu ušetřit místo ve spustitelném souboru. V řetězcový literál sdružování, přejděte příčiny kompilátoru všech odkazech na konkrétní řetězcový literál tak, aby odkazovaly do stejného umístění v paměti, místo nutnosti každý odkaz na samostatnou instanci řetězcový literál. Pokud chcete povolit sdružování řetězec, použijte [/GF](../build/reference/gf-eliminate-duplicate-strings.md) – možnost kompilátoru.  
  
 **Konkrétní Microsoft end**  
  
### <a name="concatenating-adjacent-string-literals"></a>Zřetězení přiléhající textové literály  
 Jsou zřetězeny přiléhající široké nebo úzké textové literály. Toto prohlášení:  
  
```cpp  
char str[] = "12" "34";  
```  
  
 je stejný jako tohoto prohlášení:  
  
```cpp  
char atr[] = "1234";  
```  
  
 a toto prohlášení:  
  
```cpp  
char atr[] =  "12\  
34";  
```  
  
 Použití vložených šestnáctková řídicí kódy k určení textové literály může způsobit neočekávané výsledky. V následujícím příkladu se snaží vytvořit řetězcový literál, který obsahuje znak ASCII 5, za nímž následuje znaky f, i v a e:  
  
```cpp  
"\x05five"  
```  
  
 Skutečný výsledek je hexadecimální 5F, což je kód ASCII pro podtržítkem následované znaky i, v a e. Chcete-li získat správný výsledek, použijte jednu z těchto:  
  
```cpp  
"\005five"     // Use octal literal.  
"\x05" "five"  // Use string splicing.  
```  
  
 std::String literály, protože jsou typy std::string, může být zřetězen s + – operátor, který je definován pro [basic_string](../standard-library/basic-string-class.md) typy. Může být také zřetězen stejným způsobem jako u textové literály. V obou případech se musí shodovat řetězec kódování a příponu:  
  
```cpp  
auto x1 = "hello" " " " world"; // OK  
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix  
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes  
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes  
```  
  
### <a name="string-literals-with-universal-character-names"></a>Textové literály s univerzální názvy znaků  
 Nativní (bez – hrubá, nezpracovaná) textové literály může použít univerzální názvy znaků k zastupování libovolného znaku, pokud název universal znak může být zakódován jako jeden nebo více znaků v typu řetězec.  Například název universal znaku představující znak rozšířené nemůže být kódovaný jako úzké řetězce pomocí znakové stránky ANSI, ale může být kódovaný jako úzké řetězce v některé vícebajtové znakové stránky, nebo v řetězcích UTF-8 nebo v široké řetězec. V C ++ 11, je rozšířená podpora kódování Unicode char16_t * a char32_t\* typy řetězců:  
  
```cpp  
// ASCII smiling face  
const char*     s1 = ":-)";    
  
// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)  
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";    
  
// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)  
const char*     s3 = u8"😇 = \U0001F607 is O:-)";  
  
// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)  
const char16_t* s4 = u"😃 = \U0001F603 is :-D";  
  
// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)  
const char32_t* s5 = U"😎 = \U0001F60E is B-)";  
```  
  
## <a name="see-also"></a>Viz také  
 [Znakové sady](../cpp/character-sets2.md)   
 [Číselné literály, logické a literály typu ukazatele](../cpp/numeric-boolean-and-pointer-literals-cpp.md)   
 [Uživateli definované literály](../cpp/user-defined-literals-cpp.md)