---
title: 'Postupy: rozhraní mezi kódem výjimek a ostatním kódem | Dokumentace Microsoftu'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4870258a946aaf5c86919e1fd04f574aaed4d99b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213215"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Postupy: Rozhraní mezi kódem výjimek a ostatním kódem

Tento článek popisuje, jak implementovat konzistentní zpracování výjimek v modulu jazyka C++ a také způsob převodu těchto výjimek z chybových kódů na hranicích výjimek.

Někdy musí modul C++ pracovat s kódem, který nepoužívá výjimky (kód bez výjimek). Toto rozhraní se označuje jako *hranice výjimky*. Například můžete chtít volat funkci Win32 `CreateFile` ve svém programu C++. `CreateFile` nevyvolá výjimky; Místo toho definuje kódy chyb, které je možné načíst podle `GetLastError` funkce. Pokud C++ program je netriviální, potom v něm pravděpodobně dáváte mají konzistentní zásady zpracování chyb založené na výjimku. A je pravděpodobně nebudete chtít opustit výjimky jen proto rozhraní s nevýjimečným kódem, a ani nebudete chtít míchat zásady chyb na základě výjimky a nezaložené výjimku v modulu jazyka C++.

## <a name="calling-non-exceptional-functions-from-c"></a>Volání Nevýjimečné funkce z jazyka C++

Při volání nevýjimečné funkce z jazyka C++, myšlenka je zabalit tuto funkci ve funkci jazyka C++, který zjistí všechny chyby a pak případně vyvolá výjimku. Při návrhu takové funkce obálky, nejdřív se rozhodněte, který typ záruky výjimky chcete poskytnout: bez vyvolávání, silný nebo základní. Za druhé Navrhněte funkci tak, aby všechny prostředky, například obslužné rutiny souborů, byly správně uvolněny, pokud je vyvolána výjimka. Obvykle to znamená použít inteligentní ukazatele nebo podobné správce prostředků pro vlastnění zdrojů. Další informace o zvažování návrhu naleznete v tématu [postupy: návrh pro bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje funkce jazyka C++, které používají rozhraní Win32 `CreateFile` a `ReadFile` functions interně pro otevření a čtení dvou souborů.  `File` Třída je získání prostředků je obálka inicializace (RAII) pro popisovače souborů. Jeho konstruktor rozpozná stav "soubor nebyl nalezen" a dojde k výjimce šíření chyb v zásobníku volání modulu C++ (v tomto příkladu `main()` funkce). Pokud je vyvolána výjimka po `File` objektu je plně sestaveny, destruktor automaticky volá `CloseHandle` k uvolnění popisovače souboru. (Pokud dáváte přednost, můžete použít aktivní šablony knihovny (ATL) `CHandle` třídy pro stejný účel, nebo `unique_ptr` společně s vlastním odstraňovačem.) Funkce, které volají Win32 a rozhraní API CRT detekují chyby a poté vyvolají výjimky C++ pomocí místně definované `ThrowLastErrorIf` funkce, která dále používá `Win32Exception` třídu odvozenou z `runtime_error` třídy. Všechny funkce v tomto příkladu zadejte záruku silné výjimky; Pokud v libovolném bodě těchto funkcí je vyvolána výjimka, žádných zdrojů a je upraven žádný stav programu.

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Volání výjimečného Nevýjimečným kódem

Funkce jazyka C++, které jsou deklarovány jako "extern C" mohou být volány programy c. Servery C++ COM mohou být spotřebovány kódem napsaným v některém z mnoha různých jazycích. Při implementaci veřejných funkcí podporujících výjimky v C++, které jsou volány kódem bez výjimek, nesmí funkce C++ povolit všechny výjimky zpět na volajícího. Funkce C++ proto musí konkrétně zachytit každou výjimku, kterou umí zpracovat a v případě potřeby ji převést do srozumitelného chybového kódu, který volající rozumí. Pokud jsou známy všechny potenciální výjimky, by měl mít funkce C++ `catch(...)` bloku jako poslední obslužnou rutinou. V takovém případě je nejlepší oznámit závažnou chybu volajícímu, protože váš program může být v neznámém stavu.

Následující příklad ukazuje funkci, která předpokládá, že jakoukoliv výjimku, která by mohla být vyvolána je buď Win32Exception, nebo typ výjimky odvozený z `std::exception`. Funkce zachytí jakoukoli výjimku těchto typů a šíří informace o chybě jako chybový kód Win32 k volajícímu.

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

Při převodu z výjimek na chybové kódy jedním potenciálním problémem je, že kódy chyb často neobsahují bohatost informací, které mohou ukládat výjimky. Chcete-li to vyřešit, můžete poskytnout **catch** blok pro každý typ výjimky, která by mohla být vyvolána a provádět protokolování pro zaznamenání podrobnosti o výjimce, než je převedena na chybový kód. Tento přístup může vytvořit velké množství opakování kódu, pokud více funkcí používá stejnou sadu **catch** bloky. Dobrým způsobem, jak zabránit opakování kódu, je refaktoring bloků do jedné soukromé funkce nástroje, který implementuje **zkuste** a **catch** a ostatní porty blokuje přijímá objekt funkce, která je volána v **zkuste** bloku. V každé veřejné funkci předejte kód funkci nástroje jako lambda výraz.

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

Následující příklad ukazuje, jak zapsat lambda výraz, který definuje funktor. Když je funktor definovaný "vloženě" pomocí lambda výrazu, je často čitelnější než by bylo, pokud by byl zapsán jako objekt pojmenované funkce.

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="see-also"></a>Viz také:

[Ošetření chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Postupy: Návrh s ohledem na bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md)<br/>
