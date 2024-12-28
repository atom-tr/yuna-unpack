# Yuna Unpack

An asset extractor for Epic Seven.

Original version by https://github.com/Asgarrrr, but not found now

## Installation

**[Download](https://github.com/atom-tr/yuna-unpack/archive/master.zip)** the latest version of Yuna Unpack.

## Usage

1. Get `data.pack` file

    <details>
    <summary>PC Client (STOVE)</summary>
    <ol type="1">
    <li>Locate where the game has been installed: STOVE > Settings > Game > My Game Save Folder</li>
    <li>Go to Folder > EpicSeven and locate <code>data.pack</code> file (in minimal folder is default data and in game folder is updated data) </li>
    </ol>
    </details>

    <details>
        <summary>Emulator</summary>
        <ol type="1">
            <li>First, you need to install Epic Seven on an emulator, which must allow you to access the file and transfer it to your computer. For the example, I would use Nox player.</li>
            <li>Open Nox, install Epic Seven, then launch the resource installation, and a file manager.</li>
            <li>Switch to root mode in the settings.</li>
            <li>Once the resource installation is done, go to <code>~/sdcard/com.stove.epic7.google/files/</code> and copy the <code>data.pack</code> file to <code>~/mnt/shared/Other/</code>.</li>
        </ol>
    </details>

2. Go to the Nox document sharing folder on your computer, and place the `data.pack` in the Yuna Unpack folder.

3. Install dependencies

    ```sh
    npm install
    ```

    or with `pnpm`
    
    ```sh
    pnpm install
    ```

3. Now you just have to execute the command 
    
    ```sh
    npm start
    ```

    or

    ```sh
    pnpm start
    ```

*All assets will be added to an `output` folder, sorted by category. In the `logs` folder will be generated at each runtime (if new items are detected in the data.pack) a file listing the different new items found.*

## How it works

The data.pack file contains the assets used in the game, such as images, animations, music, etc... It is initially encrypted with an XOR key of 129 byte long. This key will be applied to approximately 1073741824 byte of the data.pack.

The program will then search for all occurrences of file signatures in order to extract them.

Both files and databases have a layer of encryption that I have not yet managed to.