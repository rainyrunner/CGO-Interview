# Interview 
```package web;
import java.util.*;
import org.springframework.ui.*;
import org.springframework.stereotype.*;
import org.springframework.web.bind.annotation.*;

@RestController class Frog {
        @PostMapping(path="/frog", consumes="application/json")
        Result showResult(@RequestBody Map map) {
                //int [] leaf = {1, 3, 1, 4, 2, 3, 5, 4};
                //int block = 5;
                Result r = new Result();
                try {
                        int block = (Integer)map.get("block");
                        ArrayList a = (ArrayList)map.get("leaf");
                        int [] leaf = new int[a.size()];
                        for (int i = 0; i < a.size(); i++) {
                                leaf[i] = (Integer)a.get(i);
                        }
                        boolean [] status = new boolean[block];
                        int count = 0;
                        int i = 0;
                        while (i < leaf.length) {
                                int position = leaf[i];
                                if (position >= 0 && position < block) {
                                        if (status[position] == false) {
                                                count++;
                                                status[leaf[i]] = true;
                                        }
                                }
                                if (count == block) {r.result = i; break;}
								i++;
                        }
                } catch (Exception e) {System.out.println(e);}
                return r;
        }
}
class Result {
        public int result = -1;
}```

Nirumon Warahajeerakun
