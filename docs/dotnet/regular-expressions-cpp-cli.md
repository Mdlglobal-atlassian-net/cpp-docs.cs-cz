---
title: Regulární výrazy (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7f9937d9f93af6179d890f1e9160dd8900cd9f14
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375612"
---
# <a name="regular-expressions-ccli"></a>Regulární výrazy (C++/CLI)

Ukazuje různé operace s řetězci používání tříd regulárních výrazů v rozhraní .NET Framework.

Následující témata ukazují použití rozhraní .NET Framework <xref:System.Text.RegularExpressions> obor názvů (a v jednom případě <xref:System.String.Split%2A?displayProperty=fullName> metoda) k vyhledávání, analyzovat a úpravě řetězce.

## <a name="parse_regex"></a> Analýza řetězců využívajících regulární výrazy

Následující příklad kódu ukazuje analýzu pomocí jednoduchého řetězce <xref:System.Text.RegularExpressions.Regex> třídy v <xref:System.Text.RegularExpressions?displayProperty=fullName> oboru názvů. Řetězec obsahující různé druhy oddělovačů slov je vytvořený. Řetězec je pak analyzován pomocí <xref:System.Text.RegularExpressions.Regex> třídy ve spojení s <xref:System.Text.RegularExpressions.Match> třídy. Jednotlivých slov ve větě se pak zobrazí samostatně.

### <a name="example"></a>Příklad

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> Analýza řetězců metodou Split

Následující příklad kódu ukazuje použití <xref:System.String.Split%2A?displayProperty=fullName> metoda extrahování jednotlivých slov v řetězci. Řetězec obsahující různé druhy oddělovačů slov je vytvořen a poté analyzovat voláním <xref:System.String.Split%2A> seznam oddělovačů. Jednotlivých slov ve větě se pak zobrazí samostatně.

### <a name="example"></a>Příklad

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> Použití regulárních výrazů pro jednoduché párování

Následující příklad kódu používá regulární výrazy hledání shodného podřetězce. Vyhledávání se provádí pomocí statické <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metodu, která vezme jako vstupní údaje dva řetězce. První je řetězec, který má být prohledán a druhý je vzor, který má být vyhledán.

### <a name="example"></a>Příklad

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> Použití regulárních výrazů k extrakci datových polí

Následující příklad kódu ukazuje použití regulárních výrazů k extrakci dat z formátovaný řetězec. Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex> tak, aby určovala vzor, který odpovídá e-mailovou adresu. Tento vzorek zahrnuje pole identifikátory, které slouží k načtení uživatelů a částí názvu hostitele každou e-mailovou adresu. <xref:System.Text.RegularExpressions.Match> Třída se používá k provedení skutečné porovnávání vzorů. Pokud daného e-mailová adresa je platná, uživatelského jména a názvy hostitelů se extrahují a.

### <a name="example"></a>Příklad

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> Použití regulárních výrazů ke změně uspořádání dat

Následující příklad kódu ukazuje, jak lze podporu regulárních výrazů rozhraní .NET Framework pro uspořádání nebo opakovaně formátovat data. Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex> a <xref:System.Text.RegularExpressions.Match> třídy extrahovat jména a příjmení z řetězce a pak zobrazí tyto název prvky v obráceném pořadí.

<xref:System.Text.RegularExpressions.Regex> Třída se používá k vytvoření regulárního výrazu, která popisuje aktuální formát data. Dva názvy předpokládá, že jsou oddělené čárkou a můžete použít jakýkoli objem mezery kolem čárky. <xref:System.Text.RegularExpressions.Match> Metody se pak použije k analýze každého řetězce. V případě úspěchu, jména a příjmení se načítají z <xref:System.Text.RegularExpressions.Match> objektu a zobrazí.

### <a name="example"></a>Příklad

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> Použití regulárních výrazů k vyhledávání a nahrazení

Následující příklad kódu ukazuje, jak třídou regulárního výrazu <xref:System.Text.RegularExpressions.Regex> slouží k vyhledávání a nahrazování. Používá se k tomu <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody. Verze použitá vezme jako vstupní údaje dva řetězce: řetězec, který má být upraven a řetězec, který má být vložen místo v částech (pokud existuje), které odpovídají vzoru na <xref:System.Text.RegularExpressions.Regex> objektu.

Tento kód nahradí všechny číslice v řetězci podtržítka (_) a pak nahradí ty s prázdným řetězcem, efektivně odeberou. Stejného výsledku lze provést v jediném kroku, ale zde použijí dva kroky pro demonstrační účely.

### <a name="example"></a>Příklad

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> Použití regulárních výrazů pro ověření formátu dat

Následující příklad kódu ukazuje použití regulárních výrazů pro ověření formátování řetězce. V následujícím příkladu kódu řetězec musí obsahovat platné telefonní číslo. Následující příklad kódu používá řetězec "\d{3}-\d{3}-\d{4}" k označení, že každé pole představuje platné telefonní číslo. "D" v řetězci označuje číslici a argument po každé "d" označuje počet číslic, které musí být k dispozici. V takovém případě se číslo musí být odděleny čárkami.

### <a name="example"></a>Příklad

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>Související oddíly

[Regulárních výrazech .NET Frameworku](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)