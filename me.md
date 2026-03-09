import java.io.*;
import java.util.ArrayList;

public class WriteFile {

  private static final String FILE_NAME = "subjects.txt";

  // 書き込む
    public static void save(ArrayList<String> list) {
        try (BufferedWriter bw = new BufferedWriter(new FileWriter(FILE_NAME))) {
            for (String s : list) {
                bw.write(s);
                bw.newLine();
            }
            System.out.println("保存しました");
        } catch (IOException e) {
            System.out.println("保存エラー");
        }
    }

  // 読み込む
    public static ArrayList<String> load() {
        ArrayList<String> list = new ArrayList<>();

  try (BufferedReader br = new BufferedReader(new FileReader(FILE_NAME))) {
            String line;
            while ((line = br.readLine()) != null) {
                list.add(line);
            }
            System.out.println("読み込み完了");
        } catch (IOException e) {
            System.out.println("読み込みエラー（ファイルが無い可能性）");
        }

   return list;
    }

  // 動作確認用
    public static void main(String[] args) {
        ArrayList<String> subjects = new ArrayList<>();

  subjects.add("数学");
  subjects.add("英語");
  subjects.add("プログラミング");

  save(subjects); // 書き込み

  ArrayList<String> loaded = load(); // 読み込み

   System.out.println("=== 読み込んだ科目 ===");
        for (String s : loaded) {
            System.out.println(s);
        }
    }
}

