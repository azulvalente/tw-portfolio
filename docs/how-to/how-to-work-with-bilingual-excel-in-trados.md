# Translate a bilingual Excel file in Trados Studio

A bilingual Excel file is a spreadsheet with the source text in one column and the translation in another. For example, English in column A and Spanish in column B. This guide explains how to set up Trados Studio so that it reads those columns correctly. You can then translate or review the file in the Editor, and Trados Studio writes the translation back into the right column.

## Before you start

Make sure you have:

- Trados Studio installed.
- The Excel file (`.xlsx`) you need to work on.
- The column letters for the source text and the translation. Open the file in Excel to check them.

!!! tip
    Keep a backup copy of the original Excel file before you process it in Trados Studio.

## How Trados Studio chooses the file type

Trados Studio has more than one file type for Excel files. When you add a file, Trados Studio uses the **first enabled file type** in the list that matches the file extension. If the standard **Microsoft Excel** file type comes before **Bilingual Excel**, Trados Studio treats your file as a monolingual spreadsheet, and every cell becomes source text.

To make Trados Studio use the bilingual file type, do one of the following:

- Move **Bilingual Excel** above the other Excel file types in the list.
- Clear the check boxes of the other Excel file types.

## Configure the Bilingual Excel file type

You can change the settings for all new projects, or only for the current project.

| Scope | Where to find the settings |
| --- | --- |
| All new projects | **File > Options > File Types** |
| Current project only | **Project Settings > File Types** |

1. Go to **File Types** in the scope you need.
2. Select **Bilingual Excel** and click **Move Up** until it is above the other Excel file types. Or clear the other Excel file types.
3. Expand **Bilingual Excel** and select **Common**.
4. In **Source column**, type the letter of the source column, for example `A`.
5. In **Translation column**, type the letter of the target column, for example `B`.
6. Optional: set the other options in this section, such as a column with length limits or **Preserve target style**.
7. Click **OK**.

!!! note
    The Bilingual Excel file type handles one source column and one target column. For files with several target languages in the same sheet, look at the **Multilingual Excel FileType** app in the RWS AppStore.

## Open the file

For a quick job, open the file as a single document:

1. In the **Welcome** view, click **Open Document** and select the Excel file.
2. Check the source and target languages and click **OK**.

For a larger job, or to use project settings, create a project and add the file. In that case, configure the file type in **Project Settings** (see the table in the previous section).

## Check that the columns are correct

In the **Editor**, check that:

- The left side shows only the text from the source column.
- The right side shows the existing translations, if the target column already had content.
- Header rows and other columns don't appear as segments.

If the result doesn't look right, see [Troubleshooting](#troubleshooting).

## Translate or review

Work in the Editor as usual. You can:

- Translate empty segments with your translation memory and termbase.
- Review existing translations and change their status, for example to **Translation Approved**.
- Add comments for the requester.

## Save the target file

1. Save the document (**Ctrl+S**).
2. Click **File > Save Target As**, or press **Shift+F12**.
3. Choose a name and location for the target file.

Trados Studio writes the translations into the translation column. The source column and the rest of the spreadsheet stay the same.

!!! warning
    Trados Studio might not preserve the formatting of source and target cells, such as background colors. Check the target file in Excel before you deliver it.

## Troubleshooting

| Problem | Possible cause | Solution |
| --- | --- | --- |
| All cells appear as source text. | The standard Excel file type was used. | Move **Bilingual Excel** to the top of the list, or clear the other Excel file types. Then add the file again. |
| The source and target columns are mixed up. | The column letters are wrong. | Check the column letters in Excel and update **Source column** and **Translation column**. |
| You changed the settings but nothing happened. | You changed the settings in **Options**, but the file is in an existing project. | Change the settings in **Project Settings > File Types** and add the file again. |
| A file that is not bilingual is processed as bilingual. | **Bilingual Excel** is first in the list. | Clear **Bilingual Excel**, or move it below the standard Excel file type. |

!!! tip
    File type settings apply when Trados Studio processes the file. If you change them after you add a file, remove the file and add it again.