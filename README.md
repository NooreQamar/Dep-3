# Dep-3
• Task # 03 :
#include <iostream>
#include <fstream>
#include <string>

void compress(const std::string &inputFile, const std::string &outputFile) {
    std::ifstream inFile(inputFile);
    std::ofstream outFile(outputFile);
    if (!inFile || !outFile) return;

    char currentChar;
    int count;
    while (inFile.get(currentChar)) {
        count = 1;
        while (inFile.peek() == currentChar) {
            inFile.get();
            count++;
        }
        outFile << currentChar << count;
    }
}

void decompress(const std::string &inputFile, const std::string &outputFile) {
    std::ifstream inFile(inputFile);
    std::ofstream outFile(outputFile);
    if (!inFile || !outFile) return;

    char currentChar;
    int count;
    while (inFile >> currentChar >> count) {
        for (int i = 0; i < count; ++i) {
            outFile << currentChar;
        }
    }
}

int main() {
    compress("input.txt", "compressed.txt");
    decompress("compressed.txt", "decompressed.txt");
    return 0;
}
