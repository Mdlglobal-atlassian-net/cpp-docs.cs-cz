---
title: "Postupy: rozhraní mezi kódem výjimek a ostatním kódem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59838fa1797fc87561b081d40143693dea385668
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Postupy: Rozhraní mezi kódem výjimek a ostatním kódem
Tento článek popisuje, jak implementovat konzistentní výjimek v C++ modulu a také jak přeložit tyto výjimky do a z kódy chyb v hranicích výjimka.  
  
 V některých případech musí modulu C++ rozhraní s kódem, který nepoužívá výjimky (ostatním kód). Takového rozhraní se označuje jako *výjimka hranic*. Například můžete chtít volání funkce Win32 `CreateFile` v programu C++. `CreateFile`nepodporuje generování výjimek; Místo toho nastaví kódy chyb, které může načíst `GetLastError` funkce. Pokud vaše programu C++ netriviální, pak v ní pravděpodobně chcete mít konzistentní zásady zpracování chyb na základě výjimky. A pravděpodobně nechcete abandon výjimky právě, protože rozhraní ostatním kódem a ani chcete kombinovat zásad na základě výjimky a není určena pro výjimky Chyba v modulu C++.  
  
## <a name="calling-non-exceptional-functions-from-c"></a>Volání funkcí ostatním z jazyka C++  
 Při volání ostatním funkce z jazyka C++ na nápad je zabalit této funkce ve funkci C++, který zjistí všechny chyby a pravděpodobně vyvolá výjimku. Při návrhu obálku funkci nejprve rozhodnout, jaký typ výjimky záruku zajistit: Ne throw, silné a basic. Druhý Navrhněte funkci tak, aby všechny prostředky, například popisovače souborů, jsou vydávány správně, pokud je vyvolána výjimka. Obvykle to znamená, které umožňují chytré ukazatele nebo podobné správci prostředků vlastní prostředky. Další informace o aspektech návrhu najdete v tématu [postupy: návrh na bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje funkcí jazyka C++, které používají Win32 `CreateFile` a `ReadFile` funkce interně otevřít a přečíst si dva soubory.  `File` Třída je získávání prostředků je inicializace (RAII) obálku pro popisovače souborů. Jeho konstruktoru rozpozná stav "soubor nebyl nalezen" a vyvolá výjimku potřebný k šíření chyba zásobníkem volání modulu C++ (v tomto příkladu `main()` funkce). Pokud je vyvolána výjimka po `File` plně sestavený objekt, automaticky volání destruktoru `CloseHandle` k uvolnění popisovač souboru. (Pokud dáváte přednost, můžete použít Active šablony Library (ATL) `CHandle` třídu pro tento účel stejné nebo `unique_ptr` spolu s vlastní metoda odstranění.) Funkce, které volání Win32 a rozhraní API CRT zjištění chyby a poté vyvolat výjimky jazyka C++ pomocí místně definované `ThrowLastErrorIf` funkce, které dále používá `Win32Exception` třídy, které jsou odvozené od `runtime_error` třídy. Všechny funkce v tomto příkladu zadejte silné výjimka záruku; Pokud je vyvolána výjimka v libovolném bodě tyto funkce, jsou úniku žádné prostředky a žádné program stav je měnit.  
  
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
            cout << "*** Files are different." << endl;  
        } else {  
            cout<< "*** Files match." << endl;  
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
  
## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Volání kódu výjimečných z ostatním kódu  
 Funkce C++, které jsou deklarovány jako "extern C" lze volat programy C. Servery C++ COM mohou být spotřebovávána kód napsaný v některé z mnoha různých jazycích. Pokud implementujete veřejné výjimka deklaracemi funkce v jazyce C++ k ostatním kódem, C++ funkce nesmí umožňovat jakékoli výjimky rozšíří zpět do volající. Funkce C++ proto musí catch konkrétně každých výjimka, která věděl, že může postupy zpracování a v případě potřeby převést na kód chyby, která funguje s technologií volající výjimku. Pokud nejsou všechny potenciální výjimky jsou známé, by mělo mít funkce C++ `catch(...)` bloku jako poslední obslužná rutina. V takovém případě je nejlepší na závažnou chybu nahlásit volající, protože váš program může být v neznámém stavu.  
  
 Následující příklad ukazuje funkce, která předpokládá, že se všechny výjimky, které mohou být vyvolány Win32Exception – nebo typ výjimky odvozené z `std::exception`. Funkce zachytí všechny výjimky z těchto typů a odešlou informace o chybě jako kód chyby Win32 volajícímu.  
  
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
  
 Při převodu z výjimek na kódy chyb jeden potenciální problém je, že kódy chyb často nemáte obsahovat bohatost informace, které můžete ukládat výjimku. Chcete-li to vyřešit, můžete zadat `catch` blok pro každý typ určité výjimky, které mohou být vyvolány a protokolování zaznamenejte podrobnosti o výjimce, než je převést na kód chyby. Tuto metodu můžete vytvořit mnoho opakování kódu, pokud všechny víc funkcí použít stejnou sadu `catch` bloky. Je dobrým způsobem, jak se vyhnout opakování kódu refaktoringu tyto bloky do jednu funkci privátní nástroj, který implementuje `try` a `catch` blokuje a přijímá objekt funkce, která je volána v `try` bloku. V každé veřejné funkci předáte kód funkce nástroj jako výrazu lambda.  
  
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
  
 Následující příklad ukazuje, jak zapsat výrazu lambda, která definuje functor. Když functor definované "vložené" pomocí výrazu lambda, je často snadněji přečíst, než by bylo, pokud byly napsány jako objekt s názvem funkce.  
  
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
  
 Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Ošetření chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Postupy: Návrh s ohledem na bezpečnost výjimek](../cpp/how-to-design-for-exception-safety.md)