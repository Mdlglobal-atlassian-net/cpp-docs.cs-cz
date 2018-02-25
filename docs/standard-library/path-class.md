---
title: "Path – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e91ee287b1403b49f7a70ab3d96686650d6b2f0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="path-class"></a>path – třída
**Cesta** třída uloží objekt typu řetězec\_typu, s názvem myname sem pro účely budeme vhodné pro použití jako pathname. řetězec\_typ je synonymum pro základní\_řetězec\<value_type >, kde hodnota\_typ je synonymum pro znaky v systému Windows nebo wchar_t pod Posix.  
  
 Další informace a příklady kódu najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class path;  
```  
  
## <a name="pathappend"></a>path::append –  
  
```cpp  
template <class Source>  
path& append(const Source& source);  
   
template <class InIt>  
path& append(InIt first, InIt last);
```  
  
 Členské funkce zadaná posloupnost připojí k cesta, převést a vkládání preferred_separator podle potřeby.  
  
## <a name="pathassign"></a>path::Assign –  
  
```cpp  
template <class Source>  
path& assign(const Source& source);  
  
template <class InIt>  
path& assign(InIt first, InIt last);
```  
  
 Členské funkce nahraďte cesta zadaná posloupnost, převést podle potřeby.  
  
## <a name="pathbegin"></a>path::begin –  
  
```cpp  
iterator begin() const;
```  
  
 Vrátí path::iterator, určení první element cesty byl v názvu cesty, pokud je k dispozici.  
  
## <a name="pathcstr"></a>path::c_str  
  
```cpp  
const value_type& *c_str() const noexcept;  
```  
  
 Vrací ukazatel na první znak v cesta.  
  
## <a name="pathclear"></a>path::clear –  
  
```cpp  
void clear() noexcept;  
```  
  
 Provede mypath.clear() – členská funkce  
  
## <a name="pathcompare"></a>path::Compare –  
  
```cpp  
int compare(const path& pval) const noexcept;  
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```  
  
 Vrátí první funkce mypath.compare(pval.native()). Druhý funkce vrátí hodnotu mypath.compare(str). Vrátí třetí funkce mypath.compare(ptr).  
  
## <a name="pathconcat"></a>path::concat –  
  
```cpp  
template <class Source>  
path& concat(const Source& source);  
  
template <class InIt>  
path& concat(InIt first, InIt last);
```  
  
 Zadaná posloupnost členské funkce provést připojení k cesta, převést (ale ne vkládání oddělovač) podle potřeby.  
  
## <a name="pathconstiterator"></a>path::const_iterator  
  
```cpp  
typedef iterator const_iterator;  
```  
  
 Typ je synonymum pro iterator.  
  
## <a name="pathempty"></a>path::Empty –  
  
```cpp  
bool empty() const noexcept;  
```  
  
 Vrátí mypath.empty().  
  
## <a name="pathend"></a>path::end –  
  
```cpp  
iterator end() const;
```  
  
 Vrátí iterovat koncová sekvence z iterator typu.  
  
## <a name="pathextension"></a>path::Extension –  
  
```cpp  
path extension() const;
```  
  
 Vrátí příponu filename() X tak, aby:  
  
 Pokud X == path(".") &#124; &#124; X == path("..") nebo pokud X obsahuje bez tečky, přípona je prázdný.  
  
 Jinak Přípona začíná (a zahrnuje) nejvíce vpravo tečky.  
  
## <a name="pathfilename"></a>path::filename –  
  
```cpp  
path filename() const;
```  
  
 Vrátí komponentu kořenový adresář myname, konkrétně `empty()  path() : *--end()`. Součást může být prázdná.  
  
## <a name="pathgenericstring"></a>path::generic_string  
  
```cpp  
template <class Elem,  
    class Traits = char_traits<Elem>,  
    class Alloc = allocator<Elem>>  
  basic_string<Elem, Traits, Alloc>  
    generic_string(const Alloc& al = Alloc()) const;
  
string generic_string() const;
```  
  
 Vrátí `this->string<Elem, Traits, Alloc>(al)` s (v systému Windows), všechny zpětné lomítko převedeny na dopředné lomítko.  
  
## <a name="pathgenericu16string"></a>path::generic_u16string  
  
```cpp  
u16string generic_u16string() const;
```  
  
 Vrátí všechny zpětné lomítko u16string() s (v systému Windows) převést na dopředné lomítko.  
  
## <a name="pathgenericu32string"></a>path::generic_u32string  
  
```cpp  
u32string generic_u32string() const;
```  
  
 Vrátí všechny zpětné lomítko u32string() s (v systému Windows) převést na dopředné lomítko.  
  
## <a name="pathgenericu8string"></a>path::generic_u8string  
  
```cpp  
string generic_u8string() const;
```  
  
 Vrátí všechny zpětné lomítko u8string() s (v systému Windows) převést na dopředné lomítko.  
  
## <a name="pathgenericwstring"></a>path::generic_wstring  
  
```cpp  
wstring generic_wstring() const;
```  
  
 Vrátí všechny zpětné lomítko wstring() s (v systému Windows) převést na dopředné lomítko.  
  
## <a name="pathhasextension"></a>path::has_extension  
  
```cpp  
bool has_extension() const;
```  
  
 Returns !extension().empty().  
  
## <a name="pathhasfilename"></a>path::has_filename  
  
```cpp  
bool has_filename() const;
```  
  
 Returns !filename().empty().  
  
## <a name="pathhasparentpath"></a>path::has_parent_path  
  
```cpp  
bool has_parent_path() const;
```  
  
 Returns !parent_path().empty().  
  
## <a name="pathhasrelativepath"></a>path::has_relative_path  
  
```cpp  
bool has_relative_path() const;
```  
  
 Returns !relative_path().empty().  
  
## <a name="pathhasrootdirectory"></a>path::has_root_directory  
  
```cpp  
bool has_root_directory() const;
```  
  
 Returns !root_directory().empty().  
  
## <a name="pathhasrootname"></a>path::has_root_name  
  
```cpp  
bool has_root_name() const;
```  
  
 Returns !root_name().empty().  
  
## <a name="pathhasrootpath"></a>path::has_root_path  
  
```cpp  
bool has_root_path() const;
```  
  
 Returns !root_path().empty().  
  
## <a name="pathhasstem"></a>path::has_stem  
  
```cpp  
bool has_stem() const;
```  
  
 Returns !stem().empty().  
  
## <a name="pathisabsolute"></a>path::is_absolute  
  
```cpp  
bool is_absolute() const;
```  
  
 Pro systém Windows, funkce vrátí hodnotu has_root_name() & & has_root_directory(). Posix funkce vrátí hodnotu has_root_directory().  
  
## <a name="pathisrelative"></a>path::is_relative  
  
```cpp  
bool is_relative() const;
```  
  
 Vrátí! is_absolute().  
  
## <a name="pathiterator"></a>path::iterator  
  
```cpp  
class iterator  
   {
   // bidirectional iterator for path  
   typedef bidirectional_iterator_tag iterator_category;  
   typedef path_type value_type;  
   typedef ptrdiff_t difference_type;  
   typedef const value_type *pointer;  
   typedef const value_type& reference;  
   // ...  
   };  
```  
  
 Třída popisuje obousměrného konstantní iterator, který určuje cestu součástí myname v pořadí:  
  
1.  název kořenového adresáře, pokud je k dispozici  
  
2.  kořenový adresář, pokud je k dispozici  
  
3.  Zbývající directory elementy nadřazená cesta, pokud existuje, konče název souboru, pokud je k dispozici    
  
 Pro pval objekt zadejte cestu:  
  
1.  path::iterator X = pval.begin() označí první element cesty byl v názvu cesty, pokud je k dispozici.  
  
2.  X == pval.end() je hodnota true, pokud body X právě za koncem pořadí součástí.  
  
3. * Vrátí řetězec, který odpovídá komponentu aktuální X  
  
4.  ++ X označí další komponenta v pořadí, pokud je k dispozici.  
  
5.  – X označuje předchozí komponenty v pořadí, pokud je k dispozici.  
  
6.  Změna myname zruší platnost všech iterátory určení elementů v myname.  
  
## <a name="pathmakepreferred"></a>path::make_preferred  
  
```cpp  
path& make_preferred();
```  
  
 Členská funkce převede každý oddělovače preferred_separator podle potřeby.  
  
## <a name="pathnative"></a>path::Native  
  
```cpp  
const string_type& native() const noexcept;  
```  
  
 Vrátí myname.  
  
## <a name="pathoperator"></a>path::Operator =  
  
```cpp  
path& operator=(const path& right);
path& operator=(path&& right) noexcept;  
  
template <class Source>  
path& operator=(const Source& source);
```  
  
 První člen operátor zkopíruje right.myname myname. Druhý člen operátor přesune right.myname myname. Třetí operátor členů se chová stejně jako * to = path(source).  
  
## <a name="pathoperator"></a>path::Operator +=  
  
```cpp  
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);
  
template <class Source>  
path& operator+=(const Source& source);
  
template <class Elem>  
path& operator+=(Elem elem);
```  
  
 Členské funkce chovají stejně jako odpovídající těchto výrazů:  
  
1.  concat(Right);  
  
2.  concat(path(str));  
  
3.  concat(PTR);  
  
4.  concat (string_type (1, elem));  
  
5.  concat(Source);  
  
6.  concat(path(basic_string\<Elem>(1, elem)));  
  
## <a name="pathoperator"></a>path::Operator / =  
  
```cpp  
path& operator/=(const path& right);  
  
template <class Source>  
path& operator/=(const Source& source);
```  
  
 Členské funkce chovají stejně jako odpovídající těchto výrazů:  
  
1.  Append(Right);  
  
2.  Append(Source);  
  
## <a name="pathoperator-stringtype"></a>path::Operator string_type  
  
```cpp  
operator string_type() const;
```  
  
 Operátor členů vrátí myname.  
  
## <a name="pathparentpath"></a>path::parent_path  
  
```cpp  
path parent_path() const;
```  
  
 Vrací nadřazeného cesta součást myname, konkrétně předponu myname po odebrání filename().native() a oddělovačů okamžitě předchozí adresáře. (Stejně, pokud begin()! = end(), je kombinování všech elementů v rozsahu [begin(),--end()) použitím postupně / = – operátor.) Součást může být prázdná.  
  
## <a name="pathpath"></a>path::path –  
  
```cpp  
path();

path(const path& right);
path(path&& right) noexcept;  
  
template <class Source>  
path(const Source& source);
  
template <class Source>  
path(const Source& source, const locale& loc);
  
template <class InIt>  
path(InIt first, InIt last);
  
template <class InIt>  
path(InIt first, InIt last, const locale& loc);
```  
  
 Všechny konstruktory vytvořit myname různými způsoby:  
  
 Path() je myname().  
  
 Pro cestu (const cesta & doprava) je myname(right.myname).  
  
 Pro cestu (cesta & & správné) je myname(right.myname).  
  
 Pro šablonu\<třídy zdroje > cesta (const zdroj & zdroj) je myname(source).  
  
 Pro šablonu\<třídy zdroje > cesta (const zdroj & zdroje, const národního prostředí a umístění) je myname(source), získání všechny potřebné codecvt – omezující vlastnosti z místní  
  
 Pro šablonu\<třídy InIt > cesta (InIt první, InIt poslední) je myname (první, poslední).  
  
 Pro šablonu\<třídy InIt > cesta (InIt první, poslední, const InIt národního prostředí a umístění) je myname (první, poslední), získávání všechny potřeby codecvt – omezující vlastnosti z místní  
  
## <a name="pathpreferredseparator"></a>path::preferred_separator  
  
```cpp  
#if _WIN32_C_LIB  
static constexpr value_type preferred_separator == L'\\';  
#else // assume Posix  
static constexpr value_type preferred_separator == '/';  
#endif // filesystem model now defined  
```  
  
 Objekt konstantní dává upřednostňované znak oddělení komponenty cesty, v závislosti na operačním systému hostitele. Upozorňujeme, že se stejnou měrou povolenou ve většině případů, v části Windows používat L '/' na příslušné místo.  
  
## <a name="pathrelativepath"></a>path::relative_path  
  
```cpp  
path relative_path() const;
```  
  
 Vrátí komponentu relativní cestu myname, konkrétně příponu myname po odebrání root_path().native() a oddělovačů okamžitě následné redundantní adresáře. Součást může být prázdná.  
  
## <a name="pathremovefilename"></a>path::remove_filename  
  
```cpp  
path& remove_filename();
```  
  
## <a name="pathreplaceextension"></a>path::replace_extension –  
  
```cpp  
path& replace_extension(const path& newext = path());
```  
  
 Členská funkce nejprve Odebere příponu extension().native() myname. Pak v případě! newext.empty() & & newext [0]! = tečkou (kde je tečkou * path("."). c_str()) tečky a je připojena k myname. Pak newext se připojuje k myname.  
  
## <a name="pathreplacefilename"></a>path::replace_filename –  
  
```cpp  
path& replace_filename(const path& pval);
```  
  
 Členská funkce spustí:  
  
```cpp  
remove_filename();

*this /= pval;  
return (*this);
```  
  
## <a name="pathrootdirectory"></a>path::root_directory  
  
```cpp  
path root_directory() const;
```  
  
 Vrátí komponentu myname kořenový adresář. Součást může být prázdná.  
  
## <a name="pathrootname"></a>path::root_name  
  
```cpp  
path root_name() const;
```  
  
 Vrátí komponentu název kořenové myname. Součást může být prázdná.  
  
## <a name="pathrootpath"></a>path::root_path  
  
```cpp  
path root_path() const;
```  
  
 Vrátí komponentu kořenovou cestu myname, konkrétně root_name() / root_directory. Součást může být prázdná.  
  
## <a name="pathstem"></a>path::stem –  
  
```cpp  
path stem() const;
```  
  
 Vrátí komponentu stem myname, konkrétně filename().native() s žádné koncové extension().native() odebrat. Součást může být prázdná.  
  
## <a name="pathstring"></a>path::String  
  
```cpp  
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>  
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const; 
string string() const;
```  
  
 První členská funkce (šablony) převede pořadí uložené v cesta stejným způsobem jako:  
  
1.  String() řetězce\<char, lze použít k seskupení alokační >)  
  
2.  wstring() řetězce\<wchar_t, lze použít k seskupení alokační >)  
  
3.  u16string() řetězce\<char16_t, lze použít k seskupení alokační >)  
  
4.  u32string() řetězce\<char32_t, lze použít k seskupení alokační >)  
  
 Druhý členská funkce převede pořadí uložené v cesta k kódování podporuje v systému hostitele pro char pořadí a vrátí že je uložená v objektu typu řetězec.  
  
## <a name="pathstringtype"></a>path::string_type  
  
```cpp  
typedef basic_string<value_type> string_type;  
```  
  
 Typ je synonymum pro basic_string < value_type >.  
  
## <a name="pathswap"></a>path::swap –  
  
```cpp  
void swap(path& right) noexcept;  
```  
  
 Provede odkládacího souboru (cesta, right.mypath).  
  
## <a name="pathu16string"></a>path::u16string  
  
```cpp  
u16string u16string() const;
```  
  
 Členská funkce převede pořadí uložené v cesta ve formátu UTF-16 a vrátí že je uložená v objektu u16string typu.  
  
## <a name="pathu32string"></a>path::u32string  
  
```cpp  
u32string u32string() const;
```  
  
 Členská funkce převede pořadí uložené v cesta ve formátu UTF-32 znaků a vrátí že je uložená v objektu u32string – typ.  
  
## <a name="pathu8string"></a>path::u8string  
  
```cpp  
string u8string() const;
```  
  
 Členská funkce převede pořadí uložené v cesta na UTF-8 a vrátí že je uložená v objektu u8string typu.  
  
## <a name="pathvaluetype"></a>path::value_type  
  
```cpp  
#if _WIN32_C_LIB  
typedef wchar_t value_type;  
#else // assume Posix  
typedef char value_type;  
#endif // filesystem model now defined  
```  
  
 Typ popisuje elementy path podporuje operační systém hostitele.  
  
## <a name="pathwstring"></a>path::wstring  
  
```cpp  
wstring wstring() const;
```  
  
 Převede pořadí uložené v cesta k kódování podporuje v systému hostitele pro wchar_t pořadí a vrátí že je uložená v objektu wstring typu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<filesystem >  
  
 **Namespace:** std::experimental::filesystem
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)

