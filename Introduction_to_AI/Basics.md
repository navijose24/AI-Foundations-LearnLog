What is Artificial Intelligence(AI) ? 
    Machines mimic human intelligence - learning,reasoning,prblm-solving and decision making.

    father of ai:John McCathy

    how it works:
    data->algorithms->computational power

    key areas:
    ML:make predition based on the data and patterns
    DL:mimic human brain's neural system
    NLP:computers to understand, interpret, and generate human language
    Computer Vision:computers to "see" and interpret visual information

    types:
    artificial narrow intelligence - identify and perform specific tasks
    artificial general intelligence - learn,adopt and improve from the previous actions
    artificial super intelligence - self aware entity


The Foundations of AI
    Mathematics → logic, probability, optimization.
    Philosophy → reasoning, mind-body questions.
    Psychology → how humans think/learn.
    Neuroscience → how the brain works.
    Computer Science → algorithms, programming.
    Control Theory & Cybernetics → feedback systems, robotics.
    Linguistics → natural language understanding.


History of AI
    foundation : pre-1970
        1943->Warren McCulloch-> artifical neuron
        1950->Alan Turning->Turning test
        1956->John McCathy->Artificial intelligence term
        1950-1960 ->chatterbot ELIZA
    AI winter & resurgence : 1970-1990
        1974->lighthill report->fund cuts->ai winter
        1980->expert system->which uses human intelligence to make decisions-> commercial boom-> ai summer
        early 1990-> decline of expert systems-> 2nd ai winter
        1997->Deep Blue(IBM's super computer)->beats world chees player
    ML & DL : 2000-2010
        2000->increase in computing power ->large datasets ->ml growth
        2011->Watson(IBM)->worn the quiz show Jeopardy
              APPLE realized Siri
        2012->AlexNet->image recoginision model
        2016->AlphaGo(Google DeepMind)
    Generative ai : 2020-present
        2020->Openai->GPT 3
        2021->DALL-E -> image generation model
        2022->other LLM's 
        2024->Sora,Veo ->video gen models
        2025->Agentic AI


APPROACHES TO AI
    1.Thinking Humanly
    2.Thinking rationally
    3.Acting Humanly
    4.Acting rationally


Applications of AI
    Healthcare (diagnosis, drug discovery)
    Finance (fraud detection, trading)
    Transportation (autonomous cars)
    Education (personalized learning, tutoring systems)
    Agriculture (smart irrigation, yield prediction)
    Entertainment (Netflix/Spotify recommendations, gaming)


Intelligent Agents 
    Intelligence:Ability of a system to calculate,reason,perceive relationships and analogies,learn from experience,solve problems,  comprehend complex ideas,classify, generalize, adapt new situations.
    An agent = system that perceives (via sensors) and acts (via actuators).
    Intelligent Agents:autonomous entity which act upon an environment using sensors and actuators for achieving goals.
    rules:
    1.ability to perceive the enviornment
    2.decision must be based on observation
    3.decision results in action
    4.action must be rational.
    🌀 Example:
    Self-driving car → sensors (cameras, lidar) → agent → actuators (steering, brakes).


Nature of Environments
    Every agent works inside an environment, which can differ in nature:

    | Type                     | Meaning                           | Example                           |
    | ------------------------ | --------------------------------- | --------------------------------- |
    | **Fully observable**     | Agent can see everything          | Chess game                        |
    | **Partially observable** | Limited info                      | Self-driving car (fog, obstacles) |
    | **Deterministic**        | Actions have predictable outcomes | Solving a math equation           |
    | **Stochastic**           | Outcomes have randomness          | Poker game                        |
    | **Static**               | Doesn’t change while agent thinks | Crossword puzzle                  |
    | **Dynamic**              | Keeps changing                    | Real-time driving                 |
    | **Discrete**             | Finite actions                    | Chess                             |
    | **Continuous**           | Infinite possibilities            | Driving, painting robot           |


Good behavior: The concept of rationality
    An agent’s job is to act rationally — that means: Taking the action that maximizes its expected performance, based on current knowledge.
    💬 Example:
    A chess AI doesn’t just move any piece; it chooses the move that gives it the best chance to win.
    Key terms:
    Performance measure: How success is judged (e.g., wins in chess, fuel efficiency in cars).
    Rationality: Depends on what the agent knows, observes, and can do.

PEAS Representation
    • PEAS is a type of model on which an AI agent works upon.
    P -> performence measure
    E -> environment
    A -> actuators
    S -> sensors


Structure of Agents
    Agent = Architecture + Program
    Architecture → the hardware (like sensors & actuators)
    Agent Function → Agent function is used to map a percept to an action.
                        f: P* → A
    Program → the brain or logic that decides actions


Types of agents:
    Simple Reflex Agent – acts only on current input
    Model-based Reflex Agent – remembers past info
    Goal-based Agent – acts to reach goals
    Utility-based Agent – chooses most satisfying outcome