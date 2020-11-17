### Corpus-based chatbots

#### Retrieval-based

+ methods:

  1. return the response to the most similar turn :question:
  2. return the most similar turn

  In each case, any similarity function can be used, most commonly cosines computed either over words (using tf-idf) or over embeddings.

  Although returning the response to the most similar turn seems like a more intuitive
  algorithm, returning the most similar turn seems to work better in practice.

  Example 1:

  User: Do you like Doctor Who?
  Cleverbot: Yes, so funny
  User: What's your favorite show?
  Cleverbot: I don't have one

  --

  User query:

  q = 'Do you like Doctor Who?'

  Most similar turn:

  t = 'Do you like Doctor Strangelove?'

  method 1-grap whatever the response was to t:

  'Yes, so funny'

  method 2-return the most similar turn:

  'Do you like Doctor Strangelove?'

  --

  Example 2:

  1.
  q: 我喜欢你!
  r: 十动然拒。（C中最好的匹配是t“我喜欢你很久了”，此处返回的是C中的response(t)）
  2.
  q：我昨天碰到长者了！
  r: 你怎么碰到长者的？ 
  (C可能是这样：
  昨天我和长者一起吃蛤蟆了
  你怎么碰到长者的？
  说来话长
  此时C中最好的匹配是t“你怎么碰到长者的？”，此处直接返回t，如果返回response(t),对话就会变成：
  q:我昨天碰到长者了！
  r:说来话长）

  网友“夜尽天明”提供

+ datasets: Twitter, Weibo, movie dialog.

The Retrieval-based approach can be extended by using more features than just the
words in the q (such as words in prior turns, or information about the user), and
using any full IR ranking approach.

Instead of just using corpora of conversation, the Retrieval-based approach can be used
to draw responses from narrative (non-dialog) text (Knowledge Graph).

#### Generation-Based

The problem and modifications of the basic seq2seq models:

+ repetitive and dull responses

  This can be addressed by changing the objective function for seq2seq model training to a mutual information objective, or by modifying a beam decoder to keep more diverse responses in the beam

+ inability to model the longer prior context of the conversation. 

  This can be done by allowing the model to see prior turns, such as by using a hierarchical model that summarizes information over multiple prior turns.

+ focus on generating single responses, and so don’t tend to do a good job of continuously generating responses that cohere across multiple turns. 

  This can be addressed by using reinforcement learning, as well as techniques like adversarial networks, to learn to choose responses that make the overall conversation more natural.

#### Evaluating 

+ human evaluation
+ there are beginning to be models for automatic evaluation. 
  + The ADEM (Lowe et al., 2017a) classifier is trained on a set of responses labeled by humans with how appropriate they are, and learns to predict this label from the dialog context and the words in the system response.
  + Adversarial evaluation (Bowman et al. 2016, Kannan and evaluation
    Vinyals 2016, Li et al. 2017), inspired by the Turing test. The idea is to train a
    “Turing-like” evaluator classifier to distinguish between human-generated responses and machine-generated responses. The more successful a response generation system is at fooling this evaluator, the better the system.









