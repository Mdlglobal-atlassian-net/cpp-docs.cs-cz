---
title: 'Postupy: rozhraní mezi výjimečným a nevýjimečným kódem'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: fccc40302ab7bd43b3e6b2f87eef488c7813c9be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245611"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Postupy: rozhraní mezi výjimečným a nevýjimečným kódem

Tento článek popisuje, jak implementovat konzistentní zpracování výjimek v C++ modulu a také jak přeložit tyto výjimky do a z chybových kódů na hranicích výjimky.

V C++ některých případech musí modul používat rozhraní s kódem, který nepoužívá výjimky (nevýjimečný kód). Takové rozhraní je označováno jako *hranice výjimky*. Například může být vhodné volat funkci Win32 `CreateFile` v C++ programu. `CreateFile` nevyvolá výjimky; místo toho nastaví chybové kódy, které mohou být načteny funkcí `GetLastError`. Pokud je C++ váš program netriviální, je pravděpodobné, že budete chtít, aby byly konzistentní zásady zpracování chyb založené na výjimce. A pravděpodobně nebudete chtít opustit výjimky pouze proto, že používáte rozhraní s nevýjimečným kódem, a ani nechcete v C++ modulu kombinovat zásady chyb založené na výjimkách a nevýjimkami.

## <a name="calling-non-exceptional-functions-from-c"></a>Volání jiných než výjimečných funkcíC++

Když zavoláte nevýjimečnou funkci z C++, je výsledkem zabalení této funkce ve C++ funkci, která detekuje chyby a následně vyvolá výjimku. Při návrhu takové funkce obálky nejprve určete, který typ záruky výjimky má poskytnout: No-throw, Strong nebo Basic. Za druhé navrhněte funkci tak, aby všechny prostředky, například popisovače souborů, byly správně uvolněny, pokud je vyvolána výjimka. Obvykle to znamená, že k vlastnictví prostředků používáte inteligentní ukazatele nebo podobné správce prostředků. Další informace o požadavcích na návrh naleznete v tématu [How to: Design for Exception Safety](how-to-design-for-exception-safety.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje C++ funkce, které používají funkce Win32 `CreateFile` a `ReadFile` interně k otevření a čtení dvou souborů.  Třída `File` je obálkou získávání zdrojů (RAII) pro popisovače souborů. Jeho konstruktor detekuje podmínku "soubor nebyl nalezen" a vyvolá výjimku pro šíření chyby v zásobníku volání C++ modulu (v tomto příkladu funkce `main()`). Je-li vyvolána výjimka po úplném sestavení objektu `File`, destruktor automaticky volá `CloseHandle` a uvolní popisovač souboru. (Pokud chcete, můžete použít třídu knihovny ATL (Active Template Library) `CHandle` pro stejný účel nebo `unique_ptr` společně s vlastním nástrojem pro odstranění.) Funkce, které volají rozhraní API Win32 a CRT zjišťují chyby a poté C++ vyvolávají výjimky pomocí místně definované funkce `ThrowLastErrorIf`, která zase používá třídu `Win32Exception` odvozenou od třídy `runtime_error`. Všechny funkce v tomto příkladu poskytují záruku silné výjimky; Pokud je vyvolána výjimka v jakémkoli bodě těchto funkcí, nejsou Nevráceny žádné prostředky a nedojde ke změně stavu programu.

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

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Volání mimořádného kódu z nevýjimečného kódu

C++funkce, které jsou deklarovány jako "extern C", mohou být volány programy jazyka C. C++Servery COM mohou být spotřebovány kódem napsaným v některém z mnoha různých jazyků. Když implementujete veřejné funkce podporující výjimky v C++ , které jsou volány nevýjimečným kódem, C++ funkce nesmí umožňovat rozšíření žádné výjimky zpět volajícímu. Proto C++ funkce musí specificky zachytit všechny výjimky, které ví, jak zpracovat a v případě potřeby převést výjimku na kód chyby, který volající rozumí. Pokud ne všechny potenciální výjimky jsou známy, C++ funkce by měla mít jako poslední obslužnou rutinu `catch(...)` blok. V takovém případě je nejlepší ohlásit závažnou chybu volajícímu, protože váš program může být v neznámém stavu.

Následující příklad ukazuje funkci, která předpokládá, že jakákoliv výjimka, která může být vyvolána, je buď Win32Exception, nebo typ výjimky odvozený z `std::exception`. Funkce zachytí jakoukoli výjimku z těchto typů a šíří informace o chybě jako kód chyby Win32 volajícímu.

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

Pokud převedete z výjimek na chybové kódy, jeden z možných problémů je, že kódy chyb často neobsahují bohatou informaci, kterou může výjimka ukládat. Chcete-li to vyřešit, můžete poskytnout blok **catch** pro každý konkrétní typ výjimky, který může být vyvolán, a provést protokolování pro záznam podrobností o výjimce předtím, než je převedena na kód chyby. Tento přístup může vytvořit velké množství opakování kódu, pokud více funkcí používá stejnou sadu bloků **catch** . Dobrým způsobem, jak zabránit opakování kódu, je refaktoring těchto bloků do jedné soukromé funkce nástroje, která implementuje bloky **Try** a **catch** a přijímá objekt funkce, který je vyvolán v bloku **Try** . V každé veřejné funkci předejte kód funkci Utility jako výraz lambda.

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

Následující příklad ukazuje, jak napsat výraz lambda, který definuje funktor. Je-li funktor definován "inline" pomocí výrazu lambda, je často snazší ho přečíst, než by bylo napsáno jako objekt pojmenované funkce.

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

Další informace o výrazech lambda naleznete v tématu [lambda Expressions](lambda-expressions-in-cpp.md).

## <a name="see-also"></a>Viz také:

[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md)<br/>
[Postupy: Návrh s ohledem na bezpečnost výjimek](how-to-design-for-exception-safety.md)<br/>
