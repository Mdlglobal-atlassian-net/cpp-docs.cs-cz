---
title: Načtení řetězců do zprostředkovatele OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 19fc7b16695ebeff35462aaa2c451ff6459bb7b6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425221"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>Načtení řetězců do zprostředkovatele OLE DB

`CCustomRowset::Execute` Funkce soubor se otevře a přečte řetězce. Příjemce předá název souboru k poskytovateli voláním [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)). Zprostředkovatel přijímá název souboru a uloží je v členské proměnné `m_strCommandText`. `Execute` načte název souboru z `m_strCommandText`. Pokud název souboru je neplatný nebo není k dispozici, soubor `Execute` vrátí chybu. V opačném případě se otevře soubor a volání `fgets` pro načtení řetězců. Pro každou sadu řetězců je operace čtení, `Execute` vytvoří instanci záznam uživatele (Upravit `CCustomWindowsFile` z [ukládání řetězců ve zprostředkovateli OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) a umístí jej do pole.

Pokud soubor nejde otevřít, `Execute` musí vracet DB_E_NOTABLE. Pokud místo toho vrátí E_FAIL, zprostředkovatel nebude fungovat u mnoha příjemci a nebudou předávat OLE DB [testů shodnosti](../../data/oledb/testing-your-provider.md).

## <a name="example"></a>Příklad

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
{
public:
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
    {
        enum {
            sizeOfBuffer = 256,
            sizeOfFile = MAX_PATH
        };
        USES_CONVERSION;
        FILE* pFile = NULL;
        TCHAR szString[sizeOfBuffer];
        TCHAR szFile[sizeOfFile];
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
            }

            am.dwBookmark = ++cFiles;
            if (!m_rgRowData.Add(am))
            {
                ATLTRACE("Couldn't add data to array");
                fclose(pFile);
                return E_FAIL;
            }
        }

        if (pcRowsAffected != NULL)
            *pcRowsAffected = cFiles;
        return S_OK;
    }
};
```

Když to uděláte, váš poskytovatel by měl být připraveni zkompilovat a spustit. Testování zprostředkovatele, budete potřebovat příjemce s odpovídající funkce. [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md) ukazuje, jak vytvořit testovací příjemce. Spusťte test příjemce s tímto poskytovatelem a ověřte, že příjemce testů obdrží od zprostředkovatele správné řetězce.

Pokud jste úspěšně otestovat poskytovatele, může být vhodné k vylepšení svých funkcí implementací další rozhraní. Příklad je uveden v [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Viz také

[Implementace jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
