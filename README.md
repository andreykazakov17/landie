Реализация функции curry:

        let curry = function (fn) {
                let fnLength = fn.length;
                console.log('fnLength', fnLength);

                return function f1(...args) {
                  console.log('f1 args', args);
                  if (args.length >= fnLength) {
                    console.log('enough arguments');
                    return fn(...args);
                  } else {
                    console.log('need more arguments')
                    return function f2(...moreArgs) {
                      console.log('f2', moreArgs);
                      let newArgs = args.concat(moreArgs);
                      return f1(...newArgs);
                    };
                  }
                };
              };

              let abc = function (a, b, c) {
                return a + b + c;
              };

              let abcdef = function (a, b, c, d, e, f) {
                return a + b + c + d + e + f;
              };

              let curriedAbc = curry(abc);
              let curriedAbcdef = curry(abcdef);

              let resultAbc = curriedAbc("A", "B", "C");
              let resultAbcdef = curriedAbcdef('A', 'B', 'C')('D', 'E', 'F');


              console.log('resultAbc', resultAbc);
              console.log('resultAbcdef', resultAbcdef);
              
Модификации функции drawRating
Вариант 1:

        function drawRating(vote) {
        let rating;

        function between(x, min, max) { 
            return x >= min && x <= max; 
        }

        if (between(vote, 0, 20)) {
            rating = '★☆☆☆☆';
        }
        else if (between(vote, 20, 40)) {
            rating = '★★☆☆☆';
        }
        else if (between(vote, 40, 60)) {
            rating ='★★★☆☆';
        }
        else if (between(vote, 60, 80)) {
            rating = '★★★★☆';
        }
        else {
            rating = '★★★★★';
        }

        return 'The rating is ' + rating;
    }

    console.log(drawRating(31));
    
Вариант 2:

        function drawRating(vote) {
        let rating;

        switch(vote) {
            case (vote >= 0 && vote <= 20 && vote):
                rating = '★☆☆☆☆';
                break;
            case (vote > 20 && vote <= 40 && vote):
                rating = '★★☆☆☆';
                break;
            case (vote > 40 && vote <= 60 && vote):
                rating = '★★★☆☆';
                break;
            case (vote > 60 && vote <= 80 && vote):
                rating = '★★★★☆';
                break;
            case (vote > 80 && vote <= 100 && vote):
                rating = '★★★★★';
                break;
        }

        return 'The rating is ' + rating;
    }

    console.log(drawRating(80));
